---
title: 在后台同步和更新渐进式 Web (PWA) 应用。
description: 了解在应用未运行时如何在后台工作，以将内容与服务器同步、获取新资源或处理长时间下载。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/14/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进 Web 应用， PWA， Edge， JavaScript， 服务工作线程， 后台， 同步， 提取
ms.openlocfilehash: f8ccc35cea57ce0b60ccae8b444dfcd2ce5d57e9
ms.sourcegitcommit: aea4d6f07de1c2a4b9c2a31b821e2103df99c030
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2021
ms.locfileid: "12185771"
---
# <a name="synchronize-and-update-in-the-background"></a>在后台同步和更新

使用服务工作线程时， (PA) 在用户甚至没有使用该应用时都可以在后台工作。 这以前保留给本机应用，但现在也可供 PBA 使用，从而可以提供更好的脱机体验。

请考虑以下用例：

*   允许用户撰写邮件并随时发送（即使处于脱机状态）的电子邮件应用。
*   一个新闻应用，每天提取新文章，供用户在下次打开应用时阅读。
*   允许用户下载用于脱机收听的音乐音乐应用。

使用后台同步、定期后台同步和后台提取 API，这三种用例都有可能用于 PWA。

尽管这些 API 的名称相似，但本质上有所不同。


<!-- ====================================================================== -->
## <a name="synchronize-data-with-the-server-with-the-background-sync-api"></a>使用后台同步 API 将数据与服务器同步

允许用户继续使用应用并执行操作，即使他们处于脱机状态，也可使用后台同步 API 完成。 例如，电子邮件应用可以让用户随时撰写和发送邮件。 应用前端可以尝试立即发送消息，如果设备处于脱机状态，服务工作者可以反过来捕获失败的请求，并使用后台同步 API 延迟任务，直到连接。

使用后台同步 API 的另一个示例是在后台为用户加载内容。

> [!NOTE]
> 后台同步 API 应该用于少量数据。 它要求服务工作者在数据传输的整个持续时间内保持活动状态。 由于设备可以决定终止服务工作者以延长电池使用时间，因此 API 不应用于提取大型文件。 请[改为使用后台提取 API。](#fetch-large-files-when-the-app-or-service-worker-are-not-running-with-the-background-fetch-api)

### <a name="check-for-support"></a>检查支持

此 API 在 Microsoft Edge中可用，但应确保在运行应用的其他浏览器和设备中支持此 API。 可通过测试对象是否 `ServiceWorkerRegistration` 具有 属性来 `sync` 完成此操作：

```javascript
navigator.serviceWorker.ready.then(registration => {
    if (registration.sync) {
        // Background Sync is supported.
    } else {
        // Background Sync is not supported.
    }
});
```

若要了解有关接口 `ServiceWorkerRegistration` 的信息，请参阅 [ServiceWorkerRegistration 文档](https://developer.mozilla.org/docs/Web/API/ServiceWorkerRegistration)。

### <a name="request-a-sync"></a>请求同步

首先需要请求同步。这可以通过应用程序前端或服务工作者完成。

*   当你希望让用户负责以后同步时，从前端请求同步是不错的选择。
*   当你希望对用户透明时，从服务工作线程请求同步是不错的选择。 在这种情况下，服务工作者可以检测失败的提取请求并立即请求同步。

若要请求同步，需要 和 `ServiceWorkerRegistration` 标记名称。 在应用程序前端代码中，执行以下操作：

```javascript
async function requestBackgroundSync() {
    const registration = await navigator.serviceWorker.ready;
    await registration.sync.register('my-tag-name');
}
```

或者，从服务工作线程中，改为执行以下工作：

```javascript
async function requestBackgroundSync() {
    await self.registration.sync.register('my-tag-name');
}
```

上面的 `my-tag-name` 字符串应该是标识此同步请求的唯一标记，以便可以完成多个请求。

### <a name="react-to-the-sync-event"></a>React同步事件

只要可以使用连接并且服务工作器正在运行，就会向服务工作器发送一个事件，该服务工作器可以使用它同步 `sync` 必要的数据。 `sync`可以使用以下代码侦听事件：

```javascript
self.addEventListener('sync', event => {
    if (event.tag === 'my-tag-name') {
        event.waitUntil(doTheWork());
    }
});
```

在以上示例代码中， `sync` 事件侦听器将添加到服务工作器中。 调用侦听器时，代码会检查标记在前端中是否注册，然后调用 `doTheWork` 。 此函数应返回承诺。

通常，函数会向用户处于脱机状态时无法发送 `doTheWork` 的服务器发送信息。 将此信息存储在前端的 [IndexedDB](https://developer.mozilla.org/docs/Web/API/IndexedDB_API) 存储中可能会很有用，以便以后在执行时可以从服务工作 `doTheWork` 器中检索该信息。

有关 事件、、 和 接口详细信息， `Sync` `ServiceWorkerRegistration` `SyncManager` 请参阅后台[同步草稿规范和](https://wicg.github.io/background-sync/spec/)[后台同步 API 文档](https://developer.mozilla.org/docs/Web/API/Background_Synchronization_API)。

### <a name="demo-pwa"></a>演示PWA

[My Movie List PWA](https://quirky-rosalind-ac1e65.netlify.app/)是一个演示应用，它使用后台同步 API 在用户脱机时稍后获取电影信息。

:::image type="content" source="../media/my-movie-list-pwa-demo.png" alt-text="我的电影列表PWA演示应用。" lightbox="../media/my-movie-list-pwa-demo.png":::

若要测试功能：：

1.  安装应用。

1.  使用搜索输入字段搜索电影。

1.  脱机。

    1.  选择 **F12** 以打开 DevTools。
    1.  选择 **"**  >  **应用程序服务工作者**  >  **脱机"。**

    :::image type="content" source="../media/devtools-go-offline.png" alt-text="使用 DevTools 模拟脱机。" lightbox="../media/devtools-go-offline.png":::

1.  选择 **其中一** 个电影结果中的"更多信息"。

1.  应用程序中将显示一条消息，告知你处于脱机状态，并说明稍后将自动检索影片详细信息。

    :::image type="content" source="../media/my-movie-list-pwa-demo-offline.png" alt-text="脱机消息。" lightbox="../media/my-movie-list-pwa-demo-offline.png":::

1.  通过在 DevTools 中选择 **"** 脱机"再次联机。

1.  重新加载应用。 现在将显示影片详细信息。

对于示例代码，请转到 GitHub[上的源代码](https://github.com/captainbrosset/movies-db-pwa/)。

### <a name="debug-background-syncs-with-devtools"></a>使用 DevTools 调试后台同步

你不必脱机、联机，然后等待 Microsoft Edge 触发事件来测试后台同步代码，因为 `sync` DevTools 允许你模拟此事件。

模拟事件 `sync` ：

*  打开 DevTools (**F12**) 。
*  选择 **"应用程序**  >  **服务工作人员"。**
*  在"同步"输入字段中键入注册同步 **时所使用的标记** 名称。
*  选择" **同步"** 按钮。

:::image type="content" source="../media/devtools-simulate-background-sync.png" alt-text="在&quot;应用程序&quot;面板中模拟后台同步。" lightbox="../media/devtools-simulate-background-sync.png":::

还可以在 DevTools 中记录你的应用生成的后台同步活动。

*  打开 DevTools (**F12**) 。
*  选择 **"应用程序**  >  **后台同步"。**
*  选择 **"开始录制事件"。**

同步注册和调度显示在事件日志表中。

:::image type="content" source="../media/devtools-background-sync-log.png" alt-text="记录后台同步事件。" lightbox="../media/devtools-background-sync-log.png":::


<!-- ====================================================================== -->
## <a name="regularly-get-fresh-content-with-the-periodic-background-sync-api"></a>定期后台同步 API 定期获取新鲜内容

定期后台同步 API 允许 PWA 在后台定期检索新鲜内容，以便用户可以在稍后再次打开应用时立即访问它。 使用此 API 时，PBA 无需下载新内容 (如用户在使用应用时) 新文章) 这会降低体验速度，而是可以在更方便的时间检索它。

> [!NOTE]
> 定期同步仅在设备位于已知网络 (即) 之前已连接到的网络）时发生，Microsoft Edge 会限制同步频率以匹配用户使用该应用的频率。

### <a name="check-for-support"></a>检查支持

若要检查此 API 在运行你的应用的浏览器和设备中是否受支持，请测试 `ServiceWorkerRegistration` 对象是否具有 `periodicSync` 属性：

```javascript
navigator.serviceWorker.ready.then(registration => {
    if (registration.periodicSync) {
        // Periodic Background Sync is supported.
    } else {
        // Periodic Background Sync is not supported.
    }
});
```

### <a name="request-the-user-permission"></a>请求用户权限

定期后台同步需要用户权限。 每个应用程序仅会执行一次此操作，并且使用权限 API 完成。

```javascript
const status = await navigator.permissions.query({name: 'periodic-background-sync'});
if (status.state === 'granted') {
  // Periodic background sync can be used.
} else {
  // Periodic background sync cannot be used.
}
```

若要了解有关权限 API 的信息，请参阅权限 [API 文档](https://developer.mozilla.org/docs/Web/API/Permissions_API)。

### <a name="register-a-periodic-sync"></a>注册定期同步

若要注册定期同步，你需要定义最小间隔和唯一的标记 (以便多个定期后台同步可以注册到) 。

```javascript
async function registerPeriodicSync() {
    await registration.periodicSync.register('get-daily-news', {
        minInterval: 24 * 60 * 60 * 1000
    });
}
```

以上 `minInterval` 代码中使用的 对应于 1 天（以毫秒为单位）。 此时间间隔仅为最小间隔，Microsoft Edge在定期同步事件（如网络连接以及用户是否定期使用应用）向服务工作者发出警报之前，将考虑其他因素。

### <a name="react-to-periodic-sync-events"></a>React定期同步事件

当Microsoft Edge确定是运行定期同步的一个好时间时，它会向服务工作者 `periodicsync` 发送事件。 可以使用注册同步时指定的相同标记名称处理事件。

```javascript
self.addEventListener('periodicsync', event => {
    if (event.tag === 'get-daily-news') {
        event.waitUntil(getDailyNewsInCache());
    }
});
```

`getDailyNewsInCache`在 函数中，服务工作者可以从服务器获取新内容，并存储到缓存中。 此函数应返回一个承诺，该承诺表示同步成功还是失败。

有关 事件、、 和 接口详细信息， `PeriodicSync` `ServiceWorkerRegistration` 请参阅 Web `PeriodicSyncManager` [定期后台同步草稿规范和](https://wicg.github.io/periodic-background-sync/) [Web 定期后台同步 API 文档](https://developer.mozilla.org/docs/Web/API/Web_Periodic_Background_Synchronization_API)。

### <a name="demo-pwa"></a>演示PWA

[DevTools 使用技巧](https://devtoolstips.org/)是一PWA定期后台同步 API 的开发人员。 它每天提取新的开发人员工具提示，将它们存储在缓存中，以便用户可以在下次打开应用时访问它们，无论他们是否联机。

:::image type="content" source="../media/devtools-tips-demo.png" alt-text="DevTools 使用技巧应用。" lightbox="../media/devtools-tips-demo.png":::

转到上的[源代码GitHub。](https://github.com/captainbrosset/devtools-tips/) 特别是，应用在 [registerPeriodicSync](https://github.com/captainbrosset/devtools-tips/blob/a4a5277ee6b67e5cc61eee642bf3d9c68130094f/src/layouts/home.njk#L72) 函数中注册定期同步。  [服务工作器](https://github.com/captainbrosset/devtools-tips/blob/ebfb2c7631464149ce3cc7700d77564656971ff4/src/sw.js#L115)代码是应用侦听事件 `periodicsync` 的地方。

### <a name="debug-periodic-background-syncs-with-devtools"></a>使用 DevTools 调试定期后台同步

可以使用 DevTools 模拟 `periodicsync` 事件，而不是等待最短时间间隔。

模拟事件：

*  打开 DevTools (**F12**) 。
*  选择 **"应用程序**  >  **服务工作人员"。**
*  在"定期同步"输入字段中键入注册定期同步 **时所使用的标记** 名称。
*  选择 **"定期同步"** 按钮。

:::image type="content" source="../media/devtools-simulate-background-periodic-sync.png" alt-text="在&quot;应用程序&quot;面板中模拟定期后台同步。" lightbox="../media/devtools-simulate-background-periodic-sync.png":::

还可以在 DevTools 中记录你的应用生成的定期后台同步活动。

*  打开 DevTools (**F12**) 。
*  选择**应用程序**  >  **定期后台同步**。
*  选择 **"开始录制事件"。**

定期同步注册和调度显示在事件日志表中。

:::image type="content" source="../media/devtools-periodic-background-sync-log.png" alt-text="记录定期后台同步事件。" lightbox="../media/devtools-periodic-background-sync-log.png":::


<!-- ====================================================================== -->
## <a name="fetch-large-files-when-the-app-or-service-worker-are-not-running-with-the-background-fetch-api"></a>当应用或服务工作线程未使用后台提取 API 运行时提取大型文件

后台提取 API 允许 PWA 将大量数据的下载完全委派给浏览器引擎。 这样，应用和服务工作者不必在下载进行时运行。

此 API 对于允许用户下载大型文件的应用很有用 (例如音乐、电影或播客) 脱机用例。 由于下载被委派给浏览器引擎，浏览器引擎知道如何处理不稳定的连接甚至完全失去连接，因此它可能会在必要时暂停和恢复下载。

### <a name="check-for-support"></a>检查支持

若要检查此 API 是否受支持，请测试构造函数 `BackgroundFetchManager` 是否存在于全局对象上：

```javascript
if (self.BackgroundFetchManager) {
    // Background Fetch is supported.
} else {
    // Background Fetch is not supported.
}
```

### <a name="start-a-background-fetch"></a>启动后台提取

若要启动后台提取：

```javascript
navigator.serviceWorker.ready.then(async registration => {
    const fetch = await registration.backgroundFetch.fetch('my-download-id', fileUrls, options);
});
```

上述 `my-download-id` 应为此后台提取的唯一字符串标识符。 `fileUrls` 是要下载的文件的列表，这将是字符串 URL 数组。 `options`和 是可用于自定义浏览器中下载活动的外观的对象。

有关该函数的信息，请参阅 `fetch` [BackgroundFetchManager.fetch () ](https://developer.mozilla.org/docs/Web/API/BackgroundFetchManager/fetch) 文档和 [介绍后台提取](https://developers.google.com/web/updates/2018/12/background-fetch)。


<!-- ====================================================================== -->
## <a name="re-engage-users-with-notifications-and-badges"></a>使用通知和锁屏提醒重新吸引用户

使用通知和 App Badging API 让用户知道后台任务、下载或新鲜内容已完成，而不会中断其工作流。 使用通知和锁屏提醒可增加用户与你的应用的重新参与度。

使用 Microsoft Edge，通知与系统通知中心集成，锁屏提醒显示在任务栏的应用图标上。

若要了解如何使用这些 API，请参阅使用通知、推送通知和锁屏提醒重新吸引 [用户](./notifications-badges.md)。
