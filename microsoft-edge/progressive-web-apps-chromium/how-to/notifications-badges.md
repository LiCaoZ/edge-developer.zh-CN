---
title: 使用通知、推送通知和锁屏提醒重新吸引用户
description: 了解如何使用推送通知、通知和广告 API 在渐进 Web 应用应用中提供重新吸引 (PWA) 。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/17/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用， PWA， Edge， Windows， 推送， 通知， 锁屏提醒
ms.openlocfilehash: 9c6290d1f5af7b8f1a12dee1829fa278b2a414ba
ms.sourcegitcommit: 242e9611f73507f587d1669af24d0e3423f722dc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2021
ms.locfileid: "12087088"
---
# <a name="re-engage-users-with-notifications-push-messages-and-badges"></a>使用通知、推送通知和锁屏提醒重新吸引用户

使用后台同步、定期后台同步和后台提取，渐进 Web 应用能够在应用未运行时工作，例如更新缓存数据或在设备重新获得连接时发送消息。  若要重新吸引用户使用该应用，后台任务完成后，可以使用通知和锁屏提醒。

通知对于应用参与系统的通知中心并显示图像和文本信息非常有用。 通知对于提醒用户应用中状态的重要更改非常有用。 但是，通知通常会干扰用户的工作流，并且应该很少使用。

锁屏提醒可以更加用户友好，因此可以更频繁地使用。 锁屏提醒不会中断用户的工作流，并且对于显示少量信息（如收到的消息数）非常有用。


<!-- ====================================================================== -->
## <a name="display-notifications-in-the-action-center"></a>在操作中心显示通知

PWA 可以使用通知 API 显示 [通知](https://developer.mozilla.org/docs/Web/API/Notifications_API)。

### <a name="check-for-support"></a>检查支持

使用 API 之前，请检查它是否受支持。

```javascript
if ("Notification" in window) {
    console.log("The Notifications API is support");
}
```

### <a name="request-permission"></a>请求权限

通知 API 只能在请求用户显示消息的权限后使用。 若要请求权限，请使用 `requestPermission` 函数。 应仅为响应用户操作而完成此操作。 这是最佳做法，以避免在用户尚未与使用通知的功能交互时，通过权限提示中断用户。

```javascript
button.addEventListener("click", () => {
    Notifications.requestPermission().then(permission => {
        if (permission === "granted") {
            console.log("The user accepted!");
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

在知道 API 受支持且用户已接受通知后，可以通过创建对象来显示 `Notification` 通知：

```javascript
const notification = new Notification("Hello World!");
```

:::image type="content" source="../media/notification-text-only.png" alt-text="纯文本通知。" lightbox="../media/notification-text-only.png":::

上述代码显示纯文本通知邮件，但您也可以使用其他属性自定义邮件：

```javascript
const notification = new Notification("Hello World!", {
    body: "This is my first notification message",
    icon: "/assets/logo-192.png",
});
```

:::image type="content" source="../media/notification-with-image.png" alt-text="包含一些文本和图像的通知。" lightbox="../media/notification-with-image.png":::

还可以显示来自应用的服务工作者的通知。 这非常有用，因为服务工作者可能在你的应用未运行时工作。 若要从服务工作者发送通知，请使用 `ServiceWorkerRegistration.showNotification` 函数。

```javascript
self.registration.showNotification("Hello from the Service Worker!");
```

`showNotification`函数支持与上一示例中使用的构造函数相同的参数，以及下一节中描述的 `Notification` `actions` 属性。

### <a name="add-actions-to-notifications"></a>向通知添加操作

可以添加操作，让用户在通知中执行。 这仅在使用 函数显示的永久通知中 `ServiceWorkerRegistration.showNotification` 受支持。

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

:::image type="content" source="../media/notification-with-actions.png" alt-text="包含一些文本、图像和两个操作的通知" lightbox="../media/notification-with-actions.png":::

当用户单击其中一个操作按钮时，PWA通过侦听事件来处理 `notificationclick` 单击。  收到 `notificationclick` 事件后，关闭通知并执行一些代码：

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

若要详细了解通知操作，请参阅 MDN 的[NotificationAction。](https://developer.mozilla.org/docs/Web/API/NotificationAction)


<!-- ====================================================================== -->
## <a name="display-a-badge-on-the-app-icon"></a>在应用图标上显示锁屏提醒

PWA 可以使用应用锁屏提醒 API 在应用图标 [上显示锁屏提醒][MDNAppBadgingAPI]。 锁屏提醒可以为空，也可以包含数字。

### <a name="check-for-support"></a>检查支持

使用应用保护 API 之前，请检查它在应用运行的浏览器引擎中是否受支持。

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

:::image type="content" source="../media/app-badge-in-taskbar.png" alt-text="任务栏PWA图标，Windows锁屏提醒显示数字 42":::

`setAppBadge`函数返回一个承诺，可用于了解锁屏提醒的添加时间，并捕获潜在错误。

```javascript
navigator.setAppBadge(42).then(() => {
    console.log("The badge was added");
}).catch(e => {
    console.error("Error displaying the badge", e);
});
```

### <a name="clearing-the-badge"></a>清除锁屏提醒

若要删除应用图标上的锁屏提醒，请使用来自前端或服务工作者的以下代码。

```javascript
navigator.clearAppBadge();
```

`clearAppBadge`还会返回可用于处理潜在错误的承诺。

此外，还可以再次使用 `setAppBadge` ，但传递 `0` 为 值。

```javascript
navigator.setAppBadge(0);
```


<!-- ====================================================================== -->
## <a name="add-push-notifications-to-your-pwa"></a>将推送通知添加到PWA

若要创建PWA推送通知的组：

1.  使用推送 API 订阅 [消息传递服务](https://developer.mozilla.org/docs/Web/API/Push_API)。
1.  从服务收到消息时，使用通知 API 显示 [Toast 消息](https://developer.mozilla.org/docs/Web/API/Notifications_API)。

与服务工作人员一样，推送通知 API 是基于标准的 API。  推送通知 API 跨浏览器工作，因此代码应在支持 PA 的任何地方运行。  有关将推送消息发送到服务器上不同浏览器的信息，请参阅 [Web 推送](https://www.npmjs.com/package/web-push)。

以下步骤改编自 Mozilla 提供的服务工作者 [手册][ServiceWorkerCookbookPushRichDemo] 中的"推送丰富演示"。  本指南具有许多有用的 Web 推送和服务工作者方法。


<!-- ====================================================================== -->
### <a name="step-1---generate-vapid-keys"></a>步骤 1 - 生成 VAPID 密钥

推送通知需要 VAPID (自愿应用服务器标识) 密钥，才能将推送通知发送到 PWA 客户端。  可在线使用多个 VAPID 密钥生成器 ([例如][VapidkeysMain] ，vapidkeys.com) 。

生成密钥后，你将收到包含公钥和私钥的 JSON 对象。  保存 VAPID 密钥，供稍后在本教程中使用。

有关 VAPID 和 WebPush 的信息，请参阅 [使用 Mozilla 推送][MozillaServicesSendingVapidWebPushNotificationsPush]服务发送 VAPID 标识的 WebPush 通知。


<!-- ====================================================================== -->
### <a name="step-2---subscribe-to-push-notifications"></a>步骤 2 - 订阅推送通知

服务工作人员在服务中处理推送事件和 toast 通知PWA。  若要订阅PWA推送通知，请执行以下操作：

*   请确保你的PWA安装、激活和注册。
*   确保用于完成订阅任务的代码位于订阅任务的主要 UI 线程PWA。
*   请确保具有网络连接。

在新建推送订阅之前，Microsoft Edge检查用户是否已授予PWA接收通知的权限。

如果用户尚未向用户授予PWA权限，浏览器会提示用户获取权限。  如果用户不向浏览器授予权限，则请求将引发 `registration.pushManager.subscribe` `DOMException` ，必须处理。  有关权限管理 More on， go to [Push Notifications in Microsoft Edge][WindowsBlogsWebNotificationsEdge].

在 `pwabuilder-sw-register.js` 文件中，附加以下代码段：

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

另请参阅 [PushManager][MDNPushManager] 和 [Web 推送][NPMWebPushUsage]。


<!-- ====================================================================== -->
### <a name="step-3---listen-for-push-notifications"></a>步骤 3 - 侦听推送通知

在服务中创建订阅PWA，向服务工作者添加处理程序以响应推送事件。  推送事件从服务器发送以显示 Toast 通知。  Toast 通知显示已接收邮件的数据。  若要执行以下任一任务，必须添加 `click` 处理程序：

*   消除 Toast 通知。
*   打开窗口。
*   将焦点放在窗口上。
*   打开新窗口，将焦点放在新窗口上，以显示PWA页。

若要在 `click` 文件中添加处理程序，请为 事件和 `pwabuilder-sw.js` 事件添加以下 `push` `notificationclick` 处理程序：

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

1.  转到你的PWA `http://localhost:3000` 。。  当服务工作者激活并尝试订阅你的PWA推送通知时，Microsoft Edge提示你允许PWA显示通知。  选择 **"允许"。**

    :::image type="content" source="../media/notification-permission.png" alt-text="用于启用通知的权限对话框。" lightbox="../media/notification-permission.png":::

1.  模拟服务器端推送通知，如下所示。  在浏览器中PWA `http://localhost:3000` 打开应用后，选择 `F12` 打开 DevTools。  选择 **"**  >  **应用程序服务工作**  >  **线程**推送"以将测试推送通知发送到PWA。

    推送通知显示在任务栏附近。

    :::image type="content" source="../media/devtools-push.png" alt-text="从 DevTools 推送通知。" lightbox="../media/devtools-push.png":::

    如果未选择" ("或) Toast__ 通知，系统会在几秒钟后自动关闭它，Windows操作中心中将其排好队列。

    :::image type="content" source="../media/windows-action-center.png" alt-text="Windows操作中心中的通知。" lightbox="../media/windows-action-center.png":::


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [Web 推送通知演示][AzurewebsitesWebpushdemo]


<!-- ====================================================================== -->
<!-- external links -->
[MDNAppBadgingAPI]: https://developer.mozilla.org/docs/Web/API/Badging_API "Badging API - Web API |MDN"
[MDNPushManager]: https://developer.mozilla.org/docs/Web/API/PushManager "PushManager |MDN"
[ServiceWorkerCookbookPushRichDemo]: https://serviceworke.rs/push-rich_demo.html "推送丰富演示|ServiceWorker Cookbook"
[VapidkeysMain]: https://vapidkeys.com "安全 VAPID 密钥生成器|VapidKeys"
[MozillaServicesSendingVapidWebPushNotificationsPush]: https://blog.mozilla.org/services/2016/08/23/sending-vapid-identified-webpush-notifications-via-mozillas-push-service "通过 Mozilla 的推送服务中心发送 VAPID 标识的 WebPush |Mozilla 服务"
[WindowsBlogsWebNotificationsEdge]: https://blogs.windows.com/msedgedev/2016/05/16/web-notifications-microsoft-edge#UAbvU2ymUlHO8EUV.97 "Web 通知Microsoft Edge |Windows博客"
[NPMWebPushUsage]: https://www.npmjs.com/package/web-push#usage "用法 - Web 推送|NPM"
[AzurewebsitesWebpushdemo]: https://webpushdemo.azurewebsites.net "Web 推送通知| Microsoft Edge演示"