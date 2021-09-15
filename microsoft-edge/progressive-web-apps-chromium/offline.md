---
title: 渐进式 Web 应用中的脱机和网络连接支持
description: 了解如何使用支持技术创建复原体验，以适应不同的网络条件。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/07/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用，PWA、Edge、JavaScript、Windows、UWP、Microsoft Store
ms.openlocfilehash: 6b6031aac10161c16195c83496f8d8b5b842628e
ms.sourcegitcommit: 1c5bc4695c976805fb5acbdac3350414bf79582d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2021
ms.locfileid: "11976546"
---
# <a name="offline-and-network-connectivity-support-in-progressive-web-apps"></a>渐进式 Web 应用中的脱机和网络连接支持

多年来，组织不愿意通过本机软件大量投资基于 Web 的软件，因为 Web 应用程序依赖于稳定的网络连接。 如今，Web 平台现在提供了强大的选项，使用户能够继续工作，即使网络连接不稳定或完全脱机也是如此。

## <a name="use-the-caching-to-improve-performance-of-pwas"></a>使用缓存来提高 PBA 的性能

随着服务 [工作者的引入][MDNServiceWorker]，Web 平台添加了 `Cache` API 以提供对托管缓存资源的访问权限。 此基于承诺的 API 允许开发人员存储和检索许多 Web 资源：HTML、CSS、JavaScript、图像、JSON 等。 通常，缓存 API 在服务工作线程的上下文中使用，但它在对象的主线程中 `window` 也可用。

API 的一个常见用途是在安装服务工作器时预缓存关键资源， `Cache` 如以下代码片段所示。  

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

此代码在服务工作线程生命周期事件期间运行，它将打开一个名为 的缓存，然后在它具有指向缓存的指针时，使用 方法向它添加 `install` `static-cache` 四 `addAll()` 个资源。  通常，此方法与事件期间缓存检索 `fetch` 结合   

```javascript
self.addEventListener( "fetch", event => {
    const request = event.request,
                    url = request.url;
    
    // If we are requesting an HTML page.
    if ( request.headers.get("Accept").includes("text/html") ) {
        event.respondWith(
            // Check the cache first to see if the asset exists, and if it does, return the cached asset.
            caches.match( request )
                  .then( cached_result => {
                if ( cached_result ) {
                    return cached_result;
                }
                // If the asset is not in the cache, fallback to a network request for the asset, and proceed to cache the result.
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
                // If the network is unavailable to make a request, pull the offline page out of the cache.
                .catch(() => caches.match( "/offline/" ));
            })
        ); // end respondWith
    } // end if HTML
});
```  

只要浏览器对此网站提出请求，代码段就会在服务 `fetch` 工作器中运行。 在该事件中，有一个条件语句在请求针对 HTML 文件时运行。 服务工作线程使用 方法\ (检查该文件是否位于任何缓存 `match()` \) 。 如果缓存中存在该请求，则返回缓存的结果。 如果没有，则运行该资源的新增内容，缓存响应副本供以后 `fetch` 使用，并返回响应。 如果 `fetch` 由于网络不可用而失败，则从缓存中返回脱机页面。

此简单介绍演示如何在渐进式 Web 应用应用中使用 (PWA) 。 每个PWA不同，可能使用不同的缓存策略。 代码看起来可能有所不同，并且你可能对同一应用程序中的不同路由使用不同的缓存策略。

## <a name="use-indexeddb-in-your-pwa-to-store-structured-data"></a>在数据存储区中PWA IndexedDB 存储结构化数据

`IndexedDB` 是存储结构化数据的 API。 与 API 类似，它也是异步的，这意味着您可以在主线程中或 Web 工作线程（如服务工作线程） `Cache` 中使用它。 使用 API 在客户端上存储大量结构化数据或二进制数据（如 `IndexedDB` 加密媒体对象）。 有关详细信息，请导航到[使用 IndexedDB 上的 MDN 开始。][MDNIndexeddbApiUsing]

## <a name="understand-storage-options-for-pwas"></a>了解 PBA 的存储选项

有时，你可能需要存储少量数据，以便为用户提供更好的脱机体验。 如果是这样，你可能会发现 Web 存储的键值对系统的简单性满足您的需求。  

> [!IMPORTANT]
> Web 存储是一个同步进程，在工作线程（如服务工作线程）中不可用。 大量使用可能会给应用程序造成性能问题。 


有两种类型的 Web 存储： `localStorage` 和 `sessionStorage` 。 每个数据都作为单独的数据存储进行维护，与创建它的域隔离。 `sessionStorage` 仅在浏览会话期间保留 (例如，浏览器打开时（包括刷新和还原) ）。 `localStorage` 保留，直到代码、用户或浏览器删除数据 (例如，当可用存储限制时) 。 下面的代码段演示如何使用 `localStorage` ，这类似于如何使用 `sessionStorage` 。

```javascript
var data = {
    title: document.querySelector("[property='og:title']").getAttribute("content"),
    description: document.querySelector( "meta[name='description']" ).getAttribute("content")
};
localStorage.setItem( window.location, JSON.stringify(data) );
```  

此代码段获取有关当前页面的元数据，并存储在 JavaScript 对象中。 然后，它使用 方法将该值存储为 JSON，并 `localStorage` `setItem()` 分配一个等于当前 URL 的 `window.location` 键。 您可以使用 方法检索 `localStorage` `getItem()` 信息。 

以下代码段演示如何使用缓存来枚举缓存页面和提取元数据以执行任务，如生成链接 `localstorage` 列表。

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
    // If data exists and this page is not an offline page, assuming that offline pages have the word offline in the URL.
    if ( data && request.url.indexOf('offline') < 0  )
    {
        // Build a link and insert it into the page.
    }
}
```  

`insertOfflineLink()`方法将请求的 URL 传递给 `localStorage.getItem()` 方法以检索任何存储的元数据。 检查检索到的数据，以查看数据是否存在，如果数据存在，可以针对数据采取操作，如生成和插入标记以显示数据。

## <a name="test-for-network-connections-in-your-pwa"></a>在客户端中测试PWA

除了存储信息以便脱机使用之外，了解网络连接何时可用，以便同步数据或通知用户网络状态已更改也很有用。 使用以下选项测试网络连接。

### <a name="navigatoronline"></a>navigator.onLine  

`navigator.onLine`属性是一个布尔值，可让你了解网络的当前状态。 如果值为 `true` ，则用户处于联机状态，否则用户处于脱机状态。

### <a name="online-and-offline-events"></a>联机和脱机事件  

了解网络是否可用非常有用，但你可能想要在网络连接发生更改时采取措施。 在这种情况下，你可能想要侦听网络事件并采取措施以响应网络事件。 事件在 、 和 `window` `document` 元素上可用 `document.body` ，如以下代码片段所示。

```javascript
window.addEventListener("online",  function(){
    console.log("You are online!");
});
window.addEventListener("offline", function(){
    console.log("Oh no, you lost your network connection.");
});
```  

## <a name="see-also"></a>另请参阅  

若要了解有关管理脱机方案的信息，请导航到以下页面。  

*   [高速缓存][MDNCache]  
*   [IndexedDB][MDNIndexeddbApi]  
*   [服务工作线程][MDNServiceWorker]  
*   [Web 存储][MDNWebStorageApi]  
*   [navigator.onLine][MDNNavigatoronline]  
*   [联机和脱机事件][MDNNavigatoronlineOfflineEvents]  
*   [具有意图的请求：Caching PBA 时代的策略][AlistapartRequestIntentCachingStrategiesAgePwas]
    
<!-- links -->  

[MDNCache]: https://developer.mozilla.org/docs/Web/API/Cache "缓存|MDN"  
[MDNIndexeddbApi]: https://developer.mozilla.org/docs/Web/API/IndexedDB_API "IndexedDB API | MDN"  
[MDNIndexeddbApiUsing]: https://developer.mozilla.org/docs/Web/API/IndexedDB_API/Using_IndexedDB "使用 IndexDb - IndexDB API |MDN"  
[MDNServiceWorker]: https://developer.mozilla.org/docs/Web/API/ServiceWorker "ServiceWorker |MDN"  
[MDNWebStorageApi]: https://developer.mozilla.org/docs/Web/API/Web_Storage_API "Web 存储 API |MDN"  
[MDNNavigatoronline]: https://developer.mozilla.org/docs/Web/API/NavigatorOnLine "NavigatorOnLine |MDN"  
[MDNNavigatoronlineOfflineEvents]: https://developer.mozilla.org/docs/Web/API/NavigatorOnLine/Online_and_offline_events "联机和脱机事件 - NavigatorOnLine |MDN"  

[AbookapartGoingOffline]: https://abookapart.com/products/going-offline "由一位 |一本书分开"  

[AlistapartRequestIntentCachingStrategiesAgePwas]: https://alistapart.com/article/request-with-intent-caching-strategies-in-the-age-of-pwas "具有意图的请求：Caching Aaron Gustafson |列表分开"  
