---
title: 使用锁屏提醒、通知和推送通知重新吸引用户
description: 了解如何使用推送通知、通知和 Badging API 在渐进式 Web 应用应用中提供重新 (PWA) 。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
ms.date: 09/17/2021
ms.openlocfilehash: fedd573dad2b3e4ac008d027882673fe809ed939
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12432514"
---
# <a name="re-engage-users-with-badges-notifications-and-push-messages"></a>使用锁屏提醒、通知和推送通知重新吸引用户

渐进式 Web (PBA) 在应用未运行时能够工作，例如更新缓存中的数据，或在设备重新获得连接时发送消息。  为此，请使用以下 API，这些 API 在后台同步[PWA更新中介绍](background-syncs.md)：

*  后台同步 API
*  定期后台同步 API
*  后台提取 API

若要在后台任务完成后使用应用重新吸引用户，可以使用通知和锁屏提醒。  为此，请使用以下 API：

*  应用保护 API
*  通知 API
*  推送 API

锁屏提醒用户友好，并且可经常使用。  锁屏提醒不会中断用户的工作流，并且对于显示少量信息（如收到的消息数）非常有用。

通知对于应用参与系统的通知中心并显示图像和文本信息非常有用。  通知对于提醒用户应用中状态的重要更改非常有用。  但是，通知应很少使用，因为它们通常会干扰用户的工作流。


<!-- ====================================================================== -->
## <a name="display-a-badge-on-the-app-icon"></a>在应用图标上显示锁屏提醒

PWA 可以使用应用锁屏提醒 API 在应用图标 [上显示锁屏提醒](https://developer.mozilla.org/docs/Web/API/Badging_API)。  锁屏提醒可以为空，也可以包含数字。

### <a name="check-for-support"></a>检查支持

在使用 App Badging API 之前，首先检查应用运行在的浏览器引擎中是否支持 App Badging API，如下所示：

```javascript
if (navigator.setAppBadge) {
    console.log("The App Badging API is supported!");
}
```

### <a name="displaying-the-badge"></a>显示锁屏提醒

若要设置锁屏提醒，请使用应用前端或服务工作者中的以下代码。

```javascript
// To display an empty badge
navigator.setAppBadge();

// To display a number in the badge
navigator.setAppBadge(42);
```

:::image type="content" source="../media/app-badge-in-taskbar.png" alt-text="任务栏PWA一个Windows图标，锁屏提醒显示数字 42。":::

函数 `setAppBadge` 返回 Promise，可用于了解锁屏提醒的添加时间，并捕获潜在错误，如下所示：

```javascript
navigator.setAppBadge(42).then(() => {
    console.log("The badge was added");
}).catch(e => {
    console.error("Error displaying the badge", e);
});
```

### <a name="clearing-the-badge"></a>清除锁屏提醒

若要删除应用图标上的锁屏提醒，请使用前端或服务工作者中的以下代码：

```javascript
navigator.clearAppBadge();
```

还会 `clearAppBadge` 返回可用于处理潜在错误的 Promise。

另一种清除锁屏提醒的方式是再次调用 `setAppBadge` ，但传递 `0` 为值，这次：

```javascript
navigator.setAppBadge(0);
```


<!-- ====================================================================== -->
## <a name="display-notifications-in-the-action-center"></a>在操作中心显示通知

PWA 可以使用通知 [API 显示通知](https://developer.mozilla.org/docs/Web/API/Notifications_API)。

### <a name="check-for-support"></a>检查支持

使用 API 之前，请检查它是否受支持，如下所示：

```javascript
if ("Notification" in window) {
    console.log("The Notifications API is supported");
}
```

### <a name="request-permission"></a>请求权限

通知 API 只能在请求用户显示消息的权限后使用。 若要请求权限，请使用 `requestPermission` 函数，如下所示。

请求权限应仅为响应用户操作而完成。 这是一种最佳做法，可避免在用户尚未与使用通知的功能交互时，通过权限提示中断用户。

```javascript
button.addEventListener("click", () => {
    Notifications.requestPermission().then(permission => {
        if (permission === "granted") {
            console.log("The user accepted");
        }
    });
});
```

稍后可以再次检查权限状态：

```javascript
if (Notification.permission === "granted") {
    console.log("The user already accepted");
}
```

### <a name="display-the-notification"></a>显示通知

在知道 API 受支持且用户已接受通知后，可以通过创建对象来显示通知 `Notification` ：

```javascript
const notification = new Notification("Hello World!");
```

:::image type="content" source="../media/notification-text-only.png" alt-text="纯文本通知。":::

上述代码显示纯文本通知消息，但您也可以通过添加其他 和 属性来自定义`body``icon`邮件：

```javascript
const notification = new Notification("Hello World!", {
    body: "This is my first notification message",
    icon: "/assets/logo-192.png",
});
```

:::image type="content" source="../media/notification-with-image.png" alt-text="包含一些文本和图像的通知。":::

还可以显示来自应用的服务工作者的通知。 这非常有用，因为服务工作者可能在你的应用未运行时工作。 若要从服务工作者发送通知，请使用 `ServiceWorkerRegistration.showNotification` 函数：

```javascript
self.registration.showNotification("Hello from the Service Worker!");
```

函数 `showNotification` 支持与上一示例 `Notification` 中使用的构造函数相同的参数。  函数 `showNotification` 还支持 `actions` 属性，如下一节所述。

### <a name="add-actions-to-notifications"></a>向通知添加操作

在通知中，可以添加用户要执行的操作。  这仅在使用 函数显示的持久性通知中 `ServiceWorkerRegistration.showNotification` 受支持。

```javascript
self.registration.showNotification("Your content is ready", {
    body: "Your content is ready to be viewed. View it now?",
    icon: "/assets/logo-192.png",
    actions: [
        {
            action: "view-content",
            title: "Yes"
        },
        {
            action: "go-home",
            title: "No"
        }
    ]
});
```

:::image type="content" source="../media/notification-with-actions.png" alt-text="包含一些文本、一个图像和两个操作的通知。":::

当用户单击其中一个操作按钮时，PWA通过侦听`notificationclick`事件来处理单击。  `notificationclick`收到事件后，关闭通知并执行一些代码：

```javascript
self.addEventListener('notificationclick', event => {
    // Close the notification.
    event.notification.close();

    // React to the action.
    if (event.action === 'view-content') {
        console.log("view-content action was clicked");
    } else if (event.action === 'go-home') {
        console.log("go-home action was clicked");
    } else {
        console.log("main body of the notification was clicked");
    }
}, false);
```

若要详细了解通知操作，请参阅 [MDN 的 NotificationAction](https://developer.mozilla.org/docs/Web/API/NotificationAction) 。


<!-- ====================================================================== -->
## <a name="add-push-notifications-to-your-pwa"></a>将推送通知添加到PWA

若要创建PWA推送通知的组：：

1.  使用推送 [API 订阅消息传递服务](https://developer.mozilla.org/docs/Web/API/Push_API)。
1.  从服务收到消息时，使用通知 [API 显示 Toast 消息](https://developer.mozilla.org/docs/Web/API/Notifications_API)。

与服务工作人员一样，推送通知 API 是基于标准的 API。  推送通知 API 跨浏览器工作，因此代码应在支持 PA 的任何地方运行。  有关将推送消息发送到服务器上不同浏览器的信息，请参阅 [Web 推送](https://www.npmjs.com/package/web-push)。


<!-- ====================================================================== -->
### <a name="step-1---generate-vapid-keys"></a>步骤 1 - 生成 VAPID 密钥

推送通知需要 VAPID (自动应用程序服务器标识) 密钥，才能将推送通知发送到 PWA 客户端。  可在线使用多个 VAPID 密钥生成器 (例如，[vapidkeys.com) 。](https://vapidkeys.com)

生成密钥后，你将收到包含公钥和私钥的 JSON 对象。  保存 VAPID 密钥，供以下教程稍后使用。

有关 VAPID 和 WebPush 的信息，请参阅 [使用 Mozilla 推送服务发送 VAPID 标识的 WebPush 通知](https://blog.mozilla.org/services/2016/08/23/sending-vapid-identified-webpush-notifications-via-mozillas-push-service)。


<!-- ====================================================================== -->
### <a name="step-2---subscribe-to-push-notifications"></a>步骤 2 - 订阅推送通知

服务工作人员在服务中处理推送事件和 toast 通知PWA。  若要订阅PWA推送通知，请执行以下操作：

*   请确保服务工作器已安装、处于活动状态且已注册。
*   请确保用于完成订阅任务的代码位于用户主 UI 线程PWA。
*   请确保具有网络连接。

在新建推送订阅之前，Microsoft Edge检查用户是否已授予PWA接收通知的权限。

如果用户尚未向用户授予PWA权限，浏览器会提示用户获取权限。  如果用户未向浏览器授予权限`registration.pushManager.subscribe``DOMException`，则请求将引发 ，必须处理。  有关权限管理 More on， go to [Push Notifications in Microsoft Edge](https://blogs.windows.com/msedgedev/2016/05/16/web-notifications-microsoft-edge#UAbvU2ymUlHO8EUV.97).

在文件中 `pwabuilder-sw-register.js` ，附加以下代码：

```javascript
// Ask the user for permission to send push notifications.
navigator.serviceWorker.ready
    .then(function (registration) {
        // Check if the user has an existing subscription
        return registration.pushManager.getSubscription()
            .then(function (subscription) {
                if (subscription) {
                    return subscription;
                }

                const vapidPublicKey = "PASTE YOUR PUBLIC VAPID KEY HERE";
                return registration.pushManager.subscribe({
                    userVisibleOnly: true,
                    applicationServerKey: urlBase64ToUint8Array(vapidPublicKey)
                });
            });
    });

// Utility function for browser interoperability
function urlBase64ToUint8Array(base64String) {
    var padding = '='.repeat((4 - base64String.length % 4) % 4);
    var base64 = (base64String + padding)
        .replace(/\-/g, '+')
        .replace(/_/g, '/');

    var rawData = window.atob(base64);
    var outputArray = new Uint8Array(rawData.length);

    for (var i = 0; i < rawData.length; ++i) {
        outputArray[i] = rawData.charCodeAt(i);
    }
    return outputArray;
}
```

另请参阅 [PushManager](https://developer.mozilla.org/docs/Web/API/PushManager) 和 [Web 推送](https://www.npmjs.com/package/web-push#usage)。


<!-- ====================================================================== -->
### <a name="step-3---listen-for-push-notifications"></a>步骤 3 - 侦听推送通知

在服务中创建订阅PWA，向服务工作者添加处理程序以响应推送事件。  推送事件从服务器发送以显示 Toast 通知。  Toast 通知显示已接收邮件的数据。  若要执行以下任一任务，必须添加处理程序 `click` ：

*   消除 Toast 通知。
*   打开窗口。
*   将焦点放在窗口上。
*   打开焦点并放在新窗口上，以显示PWA页。

若要在`click`文件中添加处理程序`pwabuilder-sw.js`，请为 事件和 事件`notificationclick`添加`push`以下处理程序：

```javascript
// Respond to a server push with a user notification.
self.addEventListener('push', function (event) {
    if (Notification.permission === "granted") {
        const notificationText = event.data.text();
        const showNotification = self.registration.showNotification('Sample PWA', {
            body: notificationText,
            icon: 'images/icon512.png'
        });
        // Make sure the toast notification is displayed.
        event.waitUntil(showNotification);
    }
});

// Respond to the user selecting the toast notification.
self.addEventListener('notificationclick', function (event) {
    console.log('On notification click: ', event.notification.tag);
    event.notification.close();

    // Display the current notification if it is already open, and then put focus on it.
    event.waitUntil(clients.matchAll({
        type: 'window'
    }).then(function (clientList) {
        for (var i = 0; i < clientList.length; i++) {
            var client = clientList[i];
            if (client.url == 'http://localhost:1337/' && 'focus' in client)
                return client.focus();
        }
        if (clients.openWindow)
            return clients.openWindow('/');
    }));
});
```

<!-- ====================================================================== -->
### <a name="step-4---try-it-out"></a>步骤 4 - 试用

若要为用户测试推送通知PWA：

1.  转到你的PWA 。`http://localhost:3000`。  当服务工作者激活并尝试订阅PWA推送通知时，Microsoft Edge提示你允许PWA显示通知。  选择 **"允许"**。

    :::image type="content" source="../media/notification-permission.png" alt-text="用于启用通知的权限对话框。":::

1.  模拟服务器端推送通知，如下所示。  在浏览器中PWA`http://localhost:3000`打开应用后`F12`，选择打开 DevTools。  选择 **ApplicationService** >  **WorkerPush****** >  将测试推送通知发送到PWA。

    推送通知显示在任务栏附近。

    :::image type="content" source="../media/devtools-push.png" alt-text="从 DevTools 推送通知。":::

    如果未选择" (或) Toast 通知，系统会__ 在几秒钟后自动将其关闭，Windows操作中心中排队。

    :::image type="content" source="../media/windows-action-center.png" alt-text="Windows操作中心中的通知。":::


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [Web 推送通知演示](https://webpushdemo.azurewebsites.net)
