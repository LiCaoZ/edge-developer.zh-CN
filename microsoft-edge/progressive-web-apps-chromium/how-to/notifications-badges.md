---
title: 使用锁屏提醒、通知和推送通知重新吸引用户
description: 了解如何使用推送、通知和不良 API 在渐进式 Web 应用 (PWA) 中提供重新吸引人的功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
ms.date: 09/17/2021
ms.openlocfilehash: 52cccb1d8d11a2355ec1b2e0e672c1e39f69d807
ms.sourcegitcommit: 3c588824bd8c7484fa31acae4857405a7eec5e36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2022
ms.locfileid: "12506977"
---
# <a name="re-engage-users-with-badges-notifications-and-push-messages"></a>使用锁屏提醒、通知和推送通知重新吸引用户

渐进式Web 应用 (PVA) 能够在应用未运行时执行工作，例如更新缓存中的数据，或在设备恢复连接时发送消息。  为此，请使用以下 API，这些 API 在[后台同步和更新PWA中](background-syncs.md)所述：

*  后台同步 API
*  定期后台同步 API
*  后台提取 API

若要在完成后台任务后重新让用户参与应用，可以使用通知和徽章。  为此，请使用以下 API：

*  应用损坏 API
*  通知 API
*  推送 API

锁屏提醒是用户友好的，可以频繁使用。  锁屏提醒不会中断用户的工作流，并且对于显示少量信息（例如收到的消息数）非常有用。

通知对于应用参与系统的通知中心并显示图像和文本信息非常有用。  通知可用于提醒用户应用中状态的重大更改。  但是，应该很少使用通知，因为它们往往会对用户的工作流造成干扰。


<!-- ====================================================================== -->
## <a name="display-a-badge-on-the-app-icon"></a>在应用图标上显示徽章

PVA 可以使用 [应用损坏 API](https://developer.mozilla.org/docs/Web/API/Badging_API) 在其应用图标上显示徽章。  锁屏提醒可以为空，也可以包含数字。

### <a name="check-for-support"></a>检查支持

在使用应用损坏 API 之前，请先检查应用在运行中的浏览器引擎中是否支持应用损坏 API，如下所示：

```javascript
if (navigator.setAppBadge) {
    console.log("The App Badging API is supported!");
}
```

### <a name="displaying-the-badge"></a>显示徽章

若要设置锁屏提醒，请使用应用前端或服务辅助角色中的以下代码。

```javascript
// To display an empty badge
navigator.setAppBadge();

// To display a number in the badge
navigator.setAppBadge(42);
```

:::image type="content" source="../media/app-badge-in-taskbar.png" alt-text="Windows任务栏中的PWA图标，其中有一个显示数字 42 的徽章。":::

该 `setAppBadge` 函数返回一个 Promise，可用于知道何时添加锁屏提醒，并捕获潜在错误，如下所示：

```javascript
navigator.setAppBadge(42).then(() => {
    console.log("The badge was added");
}).catch(e => {
    console.error("Error displaying the badge", e);
});
```

### <a name="clearing-the-badge"></a>清除锁屏提醒

若要删除应用图标上的锁屏提醒，请使用前端或服务辅助角色中的以下代码：

```javascript
navigator.clearAppBadge();
```

此外，还 `clearAppBadge` 返回可用于处理潜在错误的 Promise。

清除徽章的另一种方法是再次调用 `setAppBadge` ，但传递 `0` 为值，这次：

```javascript
navigator.setAppBadge(0);
```


<!-- ====================================================================== -->
## <a name="display-notifications-in-the-action-center"></a>在操作中心显示通知

PVA 可以使用 [通知 API 显示通知](https://developer.mozilla.org/docs/Web/API/Notifications_API)。

### <a name="check-for-support"></a>检查支持

在使用 API 之前，请检查它是否受支持，如下所示：

```javascript
if ("Notification" in window) {
    console.log("The Notifications API is supported");
}
```

### <a name="request-permission"></a>请求权限

通知 API 只能在请求用户显示消息的权限后使用。 若要请求权限，请使用该 `requestPermission` 函数，如下所示。

仅应针对用户操作执行请求权限。 这是最佳做法，以避免在用户尚未与使用通知的功能交互时中断用户的权限提示。

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

知道 API 受支持且用户已接受通知后，可以通过创建 `Notification` 对象来显示通知：

```javascript
const notification = new Notification("Hello World!");
```

:::image type="content" source="../media/notification-text-only.png" alt-text="仅限文本的通知。":::

上面的代码显示一条仅限文本的通知消息，但你也可以通过包括其他 `body` 和 `icon` 属性来自定义消息：

```javascript
const notification = new Notification("Hello World!", {
    body: "This is my first notification message",
    icon: "/assets/logo-192.png",
});
```

:::image type="content" source="../media/notification-with-image.png" alt-text="包含一些文本和图像的通知。":::

还可以显示来自应用服务辅助角色的通知。 这很有用，因为服务辅助角色可能会在应用未运行时执行工作。 若要从服务辅助角色发送通知，请使用该 `ServiceWorkerRegistration.showNotification` 函数：

```javascript
self.registration.showNotification("Hello from the Service Worker!");
```

该 `showNotification` 函数支持与上一示例中使用的构造函数相同的参数 `Notification` 。  该 `showNotification` 函数还支持 `actions` 属性，如下部分所述。

### <a name="add-actions-to-notifications"></a>向通知添加操作

在通知中，可以添加操作供用户执行。  这仅在使用函数显示的持久通知中 `ServiceWorkerRegistration.showNotification` 受支持。

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

:::image type="content" source="../media/notification-with-actions.png" alt-text="包含一些文本、图像和两个操作的通知。":::

当用户单击其中一个操作按钮时，PWA可以通过侦听事件来`notificationclick`处理单击。  `notificationclick`收到事件后，关闭通知并执行一些代码：

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

若要了解有关通知操作的详细信息，请参阅 MDN 中的 [Notification.actions](https://developer.mozilla.org/docs/Web/API/notification/actions) 。


<!-- ====================================================================== -->
## <a name="add-push-notifications-to-your-pwa"></a>将推送通知添加到PWA

若要创建支持推送通知的PWA：

1.  使用 [推送 API](https://developer.mozilla.org/docs/Web/API/Push_API) 订阅消息服务。
1.  使用 [通知 API](https://developer.mozilla.org/docs/Web/API/Notifications_API) 从服务接收消息时显示 Toast 消息。

与服务辅助角色一样，推送通知 API 是基于标准的 API。  推送通知 API 可跨浏览器工作，因此代码应在支持 PVA 的任何地方工作。  有关将推送消息传送到服务器上不同浏览器的详细信息，请参阅 [Web-Push](https://www.npmjs.com/package/web-push)。


<!-- ====================================================================== -->
### <a name="step-1---generate-vapid-keys"></a>步骤 1 - 生成 VAPID 密钥

推送通知需要 VAPID (自愿应用程序服务器标识) 密钥，以便将推送消息发送到PWA客户端。  联机 (有多个 VAPID 密钥生成器，例如 [vapidkeys.com) ](https://vapidkeys.com) 。

生成密钥后，你将收到包含公钥和私钥的 JSON 对象。  保存 VAPID 密钥以供稍后在下面的教程中使用。

有关 VAPID 和 WebPush 的信息，请参 [阅使用 Mozilla 推送服务发送已识别为 VAPID 的 WebPush 通知](https://blog.mozilla.org/services/2016/08/23/sending-vapid-identified-webpush-notifications-via-mozillas-push-service)。


<!-- ====================================================================== -->
### <a name="step-2---subscribe-to-push-notifications"></a>步骤 2 - 订阅推送通知

服务工作者在PWA中处理推送事件和 toast 通知交互。  若要订阅服务器推送通知的PWA：

*   确保服务辅助角色已安装、处于活动状态并已注册。
*   请确保用于完成订阅任务的代码位于PWA的主 UI 线程上。
*   确保已建立网络连接。

在创建新的推送订阅之前，Microsoft Edge检查用户是否已授予PWA接收通知的权限。

如果用户未授予PWA接收通知的权限，则浏览器会提示用户获取权限。  如果用户未向浏览器授予权限，则请求 `registration.pushManager.subscribe` 将引发一个 `DOMException`必须处理的请求。  有关权限管理的详细信息，请转到[Microsoft Edge中的推送通知](https://blogs.windows.com/msedgedev/2016/05/16/web-notifications-microsoft-edge#UAbvU2ymUlHO8EUV.97)。

`pwabuilder-sw-register.js`在文件中，追加以下代码：

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

另请参阅 [PushManager](https://developer.mozilla.org/docs/Web/API/PushManager) 和 [Web-Push](https://www.npmjs.com/package/web-push#usage)。


<!-- ====================================================================== -->
### <a name="step-3---listen-for-push-notifications"></a>步骤 3 - 侦听推送通知

在PWA中创建订阅后，向服务辅助角色添加处理程序以响应推送事件。  推送事件从服务器发送以显示 Toast 通知。  Toast 通知显示收到的消息的数据。  若要执行以下任一任务，必须添加处理 `click` 程序：

*   关闭 Toast 通知。
*   打开窗口。
*   将焦点放在窗口上。
*   打开焦点并将其放在新窗口上，以显示PWA客户端页面。

若要添加 `click` 处理程序，请 `pwabuilder-sw.js` 在文件中为 `push` 事件和 `notificationclick` 事件添加以下处理程序：

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

若要测试PWA的推送通知：

1.  转到你的PWA。`http://localhost:3000`  当服务工作者激活并尝试订阅PWA推送通知时，Microsoft Edge会提示你允许PWA显示通知。  选择 **“允许**”。

    :::image type="content" source="../media/notification-permission.png" alt-text="用于启用通知的权限对话框。":::

1.  模拟服务器端推送通知，如下所示。  在浏览器中打开`http://localhost:3000`PWA后，选择`F12`打开 DevTools。  选择 **ApplicationService****** >  **WorkerPush** >  以向PWA发送测试推送通知。

    推送通知显示在任务栏附近。

    :::image type="content" source="../media/devtools-push.png" alt-text="从 DevTools 推送通知。":::

    如果未选择 (或_激活_ toast 通知) ，系统会在几秒钟后自动将其关闭，并在Windows操作中心中对其进行排队。

    :::image type="content" source="../media/windows-action-center.png" alt-text="操作中心Windows通知。":::


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [Web 推送通知演示](https://webpushdemo.azurewebsites.net)
