---
title: 使用服务工作人员管理网络请求和推送通知
description: 服务工作人员是 Web 工作人员，可帮助提高性能、响应不同的网络条件以及提高与 Web 应用程序的连接。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进 Web 应用，PWA、Edge、JavaScript、Windows、UWP、Microsoft Store
ms.date: 01/07/2021
ms.openlocfilehash: df05806140da3b9027443697fb5f76459e1c0297
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12286602"
---
# <a name="use-service-workers-to-manage-network-requests-and-push-notifications"></a>使用服务工作人员管理网络请求和推送通知

服务工作人员是一种特殊类型的 Web 工作线程，能够使用 API 截获、修改和响应所有网络 `Fetch` 请求。  服务工作人员可以访问 API 和异步客户端数据存储（如 ） `Cache` `IndexedDB` 来存储资源。


<!-- ====================================================================== -->
## <a name="registering-a-service-worker"></a>注册服务工作线程

与其他 Web 工作人员类似，服务工作人员必须存在于单独的文件中。 注册服务工作器时引用此文件，如以下代码所示：

```javascript
if ( "serviceWorker" in navigator ) {
    navigator.serviceWorker.register( "/serviceworker.min.js" );
}
```

新式浏览器为服务工作人员提供不同级别的支持。 因此，最佳做法是先测试对象是否存在，然后再运行任何与 `serviceWorker` 服务工作器相关的代码。 在以上代码中，使用位于网站根目录的文件注册服务 `serviceworker.min.js` 工作器。

确保将服务工作线程文件放在您希望它管理的最高级别目录中。  此类目录称为 _服务工作_ 器的范围。  在之前的代码中，文件存储在根中，服务工作者管理域中的所有页面。

如果服务工作器文件存储在目录中，则服务工作器的范围将是 `js` `js` 目录和任何子目录。  最佳做法是，将服务工作器文件放在网站的根目录下，除非需要缩小服务工作线程的范围。


<!-- ====================================================================== -->
## <a name="the-service-worker-lifecycle"></a>服务工作线程生命周期

服务工作线程的生命周期由多个步骤组成，每个步骤触发一个事件。 你可以向这些事件添加侦听器以运行代码以执行一个操作。 以下列表提供服务工作者的生命周期和相关事件的高级别视图。

1.  注册服务工作线程。

1.  浏览器下载 JavaScript 文件，安装服务工作线程，并触发 `install` 事件。 可以使用 事件预先缓存任何重要和长期的文件，如 CSS 文件、JavaScript 文件、徽标图像、脱机页面等 `install` 。

    ```javascript
    self.addEventListener( "install", function( event ){
        console.log( "WORKER: install event in progress." );
    });
    ```

1.  服务工作器将被激活，这将触发 `activate` 事件。  使用此事件清理过时的缓存。

    ```javascript
    self.addEventListener( "activate", event => {
        console.log('WORKER: activate event in progress.');
    });
    ```

1.  在刷新页面或用户转到网站上的新页面时，服务工作线程已准备好运行。 如果要在不等待的情况下运行服务工作线程，请使用 事件期间 `self.skipWaiting()` `install` 的方法，如下所示：

    ```javascript
    self.addEventListener( "install", event => {
        self.skipWaiting();
        // …
    });
    ```

1.  服务工作线程现在正在运行。


<!-- ====================================================================== -->
## <a name="using-fetch-in-service-workers"></a>在服务工作者中使用提取

在服务工作线程中使用的主要事件是 `fetch` 事件。  每次浏览器尝试访问服务工作器范围内的内容时，都会 `fetch` 运行该事件。

以下代码演示如何将侦听器添加到 fetch 事件：

```javascript
self.addEventListener( "fetch", event => {
  console.log('WORKER: Fetching', event.request);
});
```

在处理程序中，你可以控制请求是否进入网络、是否从缓存拉取 `fetch` ，等等。  您采用的方法可能有所不同，具体视所请求的资源类型、更新频率以及应用程序特有的其他业务逻辑而异。

下面是您可以在处理程序中执行哪些操作的示例 `fetch` ：

*   如果可用，则从缓存返回响应;否则，回退到通过网络请求资源。
*   从网络提取资源、缓存副本并返回响应。
*   允许用户指定保存数据的首选项。
*   为某些图像请求提供占位符图像。
*   直接在服务工作线程中生成响应。


<!-- ====================================================================== -->
## <a name="push-notifications"></a>推送通知

服务工作人员可以向用户推送通知。  推送通知可以提示用户经过一段时间后重新使用您的应用程序。  若要了解更多信息，请参阅 [使用锁屏提醒、通知和推送通知重新吸引用户](./notifications-badges.md)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [使 PA 与服务工作者脱机工作](https://developer.mozilla.org/docs/Web/Progressive_web_apps/Offline_Service_workers)
*   [如何使用通知和推送让 PWA 重新参与](https://developer.mozilla.org/docs/Web/Progressive_web_apps/Re-engageable_Notifications_Push)
