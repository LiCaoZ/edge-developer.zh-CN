---
title: 渐进式 Web 应用中的脱机和网络连接支持
description: 了解如何使用支持技术创建复原体验，以适应不同的网络条件。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/07/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用、PWA、Edge、JavaScript、Windows、UWP、Microsoft Store
ms.openlocfilehash: 36c4bafca23cac88ab292b022f157fcdd66163d5
ms.sourcegitcommit: 418eca66278525e923fecaf9cc30fc9b09bb98f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2021
ms.locfileid: "12235710"
---
# <a name="offline-and-network-connectivity-support-in-progressive-web-apps"></a>渐进式 Web 应用中的脱机和网络连接支持

多年来，组织不愿意通过本机软件大量投资基于 Web 的软件，因为 Web 应用程序依赖于稳定的网络连接。 如今，渐进式 Web (PWA) 平台提供了强大的选项，即使网络连接不稳定或脱机，用户也可以继续工作。


<!-- ====================================================================== -->
## <a name="use-caching-to-improve-pwa-performance"></a>使用缓存来提高PWA性能

随着服务 [工作者的引入](https://developer.mozilla.org/docs/Web/API/ServiceWorker)，Web 平台添加了 `Cache` API 以提供对托管缓存资源的访问权限。 此基于承诺的 API 允许开发人员存储和检索许多 Web 资源：HTML、CSS、JavaScript、图像、JSON 等。 通常，缓存 API 在服务工作线程的上下文中使用，但它在对象的主线程中 `window` 也可用。

API 的一个常见用途是安装服务工作器时预缓存关键 `Cache` 资源，如以下代码所示。

```javascript
self.addEventListener( "install", function( event ){
    event.waitUntil(
        caches.open( "static-cache" )
              .then(function( cache ){
            return cache.addAll([
                "/css/main.css",
                "/js/main.js",
                "/img/favicon.png",
                "/offline/"
            ]);
        })
    );
});
```

上述代码在服务工作线程 `install` 生命周期事件期间运行，并打开名为 的缓存 `static-cache` 。 当具有指向缓存的指针时，它会使用 方法向缓存添加四 `addAll()` 个资源。

上述方法通常与事件期间缓存检索 `fetch` 结合，如下所示：

```javascript
self.addEventListener( "fetch", event => {
    const request = event.request;
    const url = request.url;

    // If we are requesting an HTML page.
    if ( request.headers.get("Accept").includes("text/html") ) {
        event.respondWith(
            // Check the cache first to see if the asset exists, and if it does, 
            // return the cached asset.
            caches.match( request )
                  .then( cached_result => {
                if ( cached_result ) {
                    return cached_result;
                }
                // If the asset isn't in the cache, fall back to a network request 
                // for the asset, and proceed to cache the result.
                return fetch( request )
                       .then( response => {
                    const copy = response.clone();
                    // Wait until the response we received is added to the cache.
                    event.waitUntil(
                        caches.open( "pages" )
                              .then( cache => {
                            return cache.put( request, response );
                        });
                    );
                    return response;
                })
                // If the network is unavailable to make a request, pull the offline
                // page out of the cache.
                .catch(() => caches.match( "/offline/" ));
            })
        ); // end respondWith
    } // end if HTML
});
```

只要浏览器对此网站提出请求，上述代码就会在服务 `fetch` 工作器中运行。 在该事件中，有一个条件语句在请求针对 HTML 文件时运行。 服务工作线程使用 方法检查文件是否已存在于任何缓存 `match()` 中：

*  如果缓存中存在该请求，则返回缓存的结果。
*  如果缓存中不存在该请求，将运行该资源的新请求，稍后将缓存响应的副本，并 `fetch` 返回响应。
   * 如果 `fetch` 由于网络不可用而失败，则从缓存中返回脱机页面。

此简单介绍演示如何在渐进式 Web 应用应用中使用 (PWA) 。 每个PWA不同，可能使用不同的缓存策略。 代码看起来可能不同，并且你可以对同一应用程序中的不同路由使用不同的缓存策略。


<!-- ====================================================================== -->
## <a name="use-indexeddb-in-your-pwa-to-store-structured-data"></a>在数据存储区中PWA IndexedDB 存储结构化数据

`IndexedDB` 是存储结构化数据的 API。 与 `Cache` API 类似，它也是异步的。 这意味着您可以在主线程中或与 Web 工作线程（如服务工作线程）一起使用它。 使用 API 在客户端上存储大量结构化数据或二进制数据（如 `IndexedDB` 加密媒体对象）。  有关 [使用 IndexedDB，请参阅 MDN 一文](https://developer.mozilla.org/docs/Web/API/IndexedDB_API/Using_IndexedDB)。


<!-- ====================================================================== -->
## <a name="understand-storage-options-for-pwas"></a>了解 PBA 的存储选项

有时，你可能需要存储少量数据，以便为用户提供更好的脱机体验。 如果是这样，您可能会发现 Web 应用程序键值对系统的简单性存储您的需求。

> [!IMPORTANT]
> Web 存储是一个同步进程，不能用于工作线程，如服务工作线程。 大量使用 Web 存储可能会导致应用程序的性能问题。

有两种类型的 Web 存储： 和 `localStorage` `sessionStorage` 。 每种类型的 Web 存储都作为独立于创建它的域的单独数据存储进行维护。

*  `sessionStorage` 仅在浏览会话期间保留。 例如，当浏览器打开（包括刷新和还原）时。
*  `localStorage` 保留，直到代码、用户或浏览器删除数据。 例如，当存在可用的有限存储时。

以下代码演示如何使用 `localStorage` ，这类似于如何使用 `sessionStorage` ：

```javascript
var data = {
    title: document.querySelector("[property='og:title']").getAttribute("content"),
    description: document.querySelector( "meta[name='description']" ).getAttribute("content")
};
localStorage.setItem( window.location, JSON.stringify(data) );
```

上面的代码会获取当前页面的元数据，并存储到 JavaScript 对象中。 然后，它使用 方法将该值存储为 JSON，并 `localStorage` `setItem()` 分配一个等于当前 URL 的 `window.location` 键。 您可以使用 方法从 `localStorage` 中检索 `getItem()` 信息。

以下代码演示如何使用缓存来枚举缓存页面和提取元数据以执行任务，例如生成 `localstorage` 链接列表。

```javascript
caches.open( "pages" )
      .then( cache => {
    cache.keys()
         .then( keys => {
        if ( keys.length )
        {
            keys.forEach( insertOfflineLink );
        }
    })
});

function insertOfflineLink( request ) {
    var data = JSON.parse( localStorage.getItem( request.url ) );
    // If data exists and this page isn't an offline page (assumes that offline 
    // pages have the word "offline" in the URL).
    if ( data && request.url.indexOf('offline') < 0  )
    {
        // Build a link and insert it into the page.
    }
}
```

`insertOfflineLink()`方法将请求的 URL 传递给 `localStorage.getItem()` 方法以检索任何存储的元数据。 检查检索到的数据，以查看数据是否存在，如果数据存在，可以针对数据采取操作，如生成和插入标记以显示数据。


<!-- ====================================================================== -->
## <a name="test-for-network-connections-in-your-pwa"></a>测试连接中的网络连接PWA

除了存储信息以便脱机使用之外，了解网络连接何时可用，以便同步数据或通知用户网络状态已更改也很有用。

使用以下选项测试网络连接：

### <a name="navigatoronline"></a>navigator.onLine

`navigator.onLine`属性是一个布尔值，可让你了解网络的当前状态。 如果值为 `true` ，则用户处于联机状态;否则，用户处于脱机状态。

### <a name="online-and-offline-events"></a>联机和脱机事件

可以在网络连接发生更改时采取措施。  你可以侦听网络事件并采取措施以响应网络事件。  事件在 、 和 `window` `document` `document.body` 元素上可用，如下所示：

```javascript
window.addEventListener("online",  function(){
    console.log("You are online!");
});
window.addEventListener("offline", function(){
    console.log("Oh no, you lost your network connection.");
});
```


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [高速缓存](https://developer.mozilla.org/docs/Web/API/Cache)
*   [IndexedDB](https://developer.mozilla.org/docs/Web/API/IndexedDB_API)
*   [服务工作线程](https://developer.mozilla.org/docs/Web/API/ServiceWorker)
*   [Web 存储](https://developer.mozilla.org/docs/Web/API/Web_Storage_API)
*   [navigator.onLine](https://developer.mozilla.org/docs/Web/API/NavigatorOnLine)
*   [联机和脱机事件](https://developer.mozilla.org/docs/Web/API/NavigatorOnLine/Online_and_offline_events)
*   [具有意图的请求：Caching时的策略](https://alistapart.com/article/request-with-intent-caching-strategies-in-the-age-of-pwas)
