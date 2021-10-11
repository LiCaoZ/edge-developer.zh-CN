---
title: 与其他应用共享
description: 了解如何与其他应用共享来自PWA内容并接受来自其他应用的共享内容。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/27/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用， PWA， Edge， JavaScript， 共享
ms.openlocfilehash: a4b46de09e5e49650610271ccec2e800590d3554
ms.sourcegitcommit: 242e9611f73507f587d1669af24d0e3423f722dc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2021
ms.locfileid: "12087266"
---
# <a name="share-with-other-apps"></a>与其他应用共享

在应用之间共享内容由移动设备所热门，其中操作文件或复制内容不如在桌面操作系统上直观。 在移动电话上，通常使用短信与好友共享图像。

但是共享内容不再保留给移动设备，并且也有可能在移动设备上的应用之间Windows。

共享内容有两个方面，并且两者都可以由 PWA 使用。

*   共享内容：PWA生成内容 (文本、链接或文件时) 将内容传输给操作系统，让用户决定要使用哪个应用接收该内容。
*   接收共享内容：当PWA用作在操作系统级别注册的内容目标时。

注册为共享目标的 PWA 感觉与操作系统的本机集成性更明显，并且更吸引用户。


<!-- ====================================================================== -->
## <a name="sharing-content"></a>共享内容

PWA 可以使用 [Web 共享 API][MDNWebShareAPI] 触发操作系统共享对话框。

> [!NOTE]
> Web 共享仅适用于通过 HTTPS 服务的网站 (PBA) 的情况，并且只能调用它以响应用户操作。

若要共享链接、文本或文件等内容，请使用 `navigator.share` 函数。 函数接受至少应具有以下属性之一的对象：

*   `title`：共享内容的短标题。
*   `text`：共享内容的较长说明。
*   `url`：要共享的资源的地址。
*   `files`：要共享的文件数组。

```javascript
function shareSomeContent(title, text, url) {
  if (!navigator.share) {
    return;
  }

  navigator.share({title, text, url}).then(() => {
    console.log('The content was shared successfully');
  }).catch(error => {
    console.error('Error sharing the content', error);
  });
}
```

在以上代码段中，我们首先检查浏览器是否支持 Web 共享（如果 `navigator.share` 已定义）。 函数 `navigator.share` 返回一个承诺，该承诺在共享成功时解析，在出现错误时拒绝。

因为此处使用了承诺，所以可以使用 函数 `async` 重写此代码。

```javascript
async function shareSomeContent(title, text, url) {
  if (!navigator.share) {
    return;
  }

  try {
    await navigator.share({title, text, url});
    console.log('The content was shared successfully');
  } catch (e) {
    console.error('Error sharing the content', e);
  }
}
```

在Windows，上述代码将触发共享对话框，允许用户选取应用以接收共享内容。

:::image type="content" source="../media/windows-share-dialog.png" alt-text="&quot;共享&quot;对话框Windows。" lightbox="../media/windows-share-dialog.png":::

用户选择应用接收共享内容后，由该应用以任何方式处理它。 例如，电子邮件应用可能将 用作 `title` 电子邮件主题，将 用作 `text` 正文。

### <a name="sharing-files"></a>共享文件

函数 `navigator.share` 还接受用于 `files` 与其他应用共享文件的数组。

在共享文件之前，测试共享文件是否受浏览器支持，这一点很重要。 若要检查是否支持共享文件，请使用 `navigator.canShare` 函数。

```javascript
function shareSomeFiles(files) {
  if (navigator.canShare && navigator.canShare({files})) {
    console.log('Sharing files is supported');
  } else {
    console.error('Sharing files is not supported');
  }
}
```

`files`共享对象成员必须是对象 `File` 数组。 了解有关文件 [接口的更多信息][MDNFileInterface]。

构造对象的一种方式是使用 API 请求资源，然后使用返回的响应新建， `File` `fetch` `File` 如下所示。

```javascript
async function getImageFileFromURL(imageURL, title) {
  const response = await fetch(imageURL);
  const blob = await response.blob();
  return new File([blob], title, {type: blob.type});
}
```

在以上代码段中，函数使用其 URL 提取图像，然后使用 函数将其转换为 Blob 对象，该对象可用于 `getImageFileFromURL` `response.blob()` 创建 `File` 对象。

### <a name="demo"></a>演示版

[DevTools 使用技巧][DemoDevToolsTips]是PWA函数共享文本 `navigator.share` 和链接的一个工具。

若要测试功能：：

*  转到[DevTools 使用技巧][DemoDevToolsTips]。
*  选择主页上显示的任何提示。
*  选择 **"共享提示"。**

:::image type="content" source="../media/devtools-tips-share.png" alt-text="&quot;Windows共享&quot;对话框允许用户选取要共享内容的应用。" lightbox="../media/devtools-tips-share.png":::

可以在上[找到源代码GitHub。][DemoDevToolsTipsGitHub] 特别是，应用程序使用 Web 共享 API 在 [share.js源文件中 ][DemoDevToolsTipsShareFunction] 。


<!-- ====================================================================== -->
## <a name="receiving-shared-content"></a>接收共享内容

通过使用 Web 共享目标 API，PWA 还可以注册为在系统共享对话框中显示为应用，并处理来自其他应用的共享内容。 可以在 Web 共享目标 API [W3C][W3CWebShareTargetAPI]规范草稿中了解有关 Web 共享目标 API 的信息。

> [!NOTE]
> 只有已安装的 PWA 才能注册为共享目标。

### <a name="register-as-a-target"></a>注册为目标

首先，将你的PWA注册为共享目标。 若要注册，请使用 `share_target` 清单成员。 安装应用后，操作系统将使用 成员将你的应用包括在系统共享对话框中，并知道在用户选取应用时 `share_target` 要执行哪些操作。

`share_target`成员必须包含系统将共享内容传递到应用的必要信息。 请考虑以下清单代码。

```json
{
    "share_target": {
        "action": "/handle-shared-content/",
        "method": "GET",
        "params": {
            "title": "title",
            "text": "text",
            "url": "url",
        }
    }
}
```

当用户选取你的应用作为共享内容的目标时，PWA 将启动，并且对属性指定的 URL 进行 HTTP 请求，共享数据将传递为 、 和 `GET` `action` `title` `text` `url` 查询参数。 实际上，会提出以下请求 `/handle-shared-content/?title=shared title&text=shared text&url=shared url` ：。

如果已有使用这些其他名称的代码，可以将默认 、 和 `title` `text` 查询参数 `url` 映射到其他名称。

```json
{
    "share_target": {
        "action": "/handle-shared-content/",
        "method": "GET",
        "params": {
            "title": "subject",
            "text": "body",
            "url": "address",
        }
    }
}
```

### <a name="handle-get-shared-data"></a>处理 GET 共享数据

若要处理在代码代码中通过 GET 请求PWA数据，请使用构造函数 `URL` 提取查询参数。

```javascript
window.addEventListener('DOMContentLoaded', () => {
    console url = new URL(window.location);

    const sharedTitle = url.searchParams.get('title');
    const sharedText = url.searchParams.get('text');
    const sharedUrl = url.searchParams.get('url');
});
```

### <a name="handle-post-shared-data"></a>处理 POST 共享数据

如果共享数据旨在以任何方式更改你的应用，例如通过更新应用中存储的一些内容，则必须使用 方法并使用 定义 `POST` 编码类型 `enctype` 。

```json
{
    "share_target": {
        "action": "/post-shared-content",
        "method": "POST",
        "enctype": "multipart/form-data",
        "params": {
            "title": "title",
            "text": "text",
            "url": "url",
        }
    }
}
```

`POST`HTTP 请求将包含编码为 的共享数据 `multipart/form-data` 。 可以使用服务器端代码在 HTTP 服务器上访问此数据，但当用户处于脱机状态时，这不起作用。 为了提供更好的体验，可以使用事件侦听器访问服务工作器 `fetch` 中的数据。

```javascript
self.addEventListener('fetch', event => {
    const url = new URL(event.request.url);

    if (event.request.method === 'POST' && url.pathname === '/post-shared-content') {
        event.respondWith((async () => {
            const data = await event.request.formData();

            const title = data.get('title');
            const text = data.get('text');
            const url = data.get('url');

            // Do something with the shared data here.

            return Response.redirect('/content-shared-success', 303);
        })());
    }
});
```

在以上代码段中，服务工作者截获请求，以某种方式使用数据 (例如本地存储内容（例如) ）以及将用户重定向到成功 `POST` 页面。 这样，即使网络关闭，应用也可以运行。 它可以选择仅本地存储内容，或在连接恢复时将其发送到服务器 (例如，使用后台[同步) 。][BackgroundSync]

### <a name="handle-files"></a>处理文件

应用还可以处理共享文件。 若要处理文件PWA，必须使用 `POST` 方法和编码 `multipart/form-data` 类型。 此外，你必须声明你的应用可以处理的文件类型。

```json
{
    "share_target": {
        "action": "/store-code-snippet",
        "method": "POST",
        "enctype": "multipart/form-data",
        "params": {
            "title": "title",
            "files": [
                {
                    "name": "textFile",
                    "accept": ["text/plain", "text/html", "text/css", "text/javascript"]
                }
            ]
        }
    }
}
```

上述清单代码告知系统你的应用可以接受各种 mime 类型的文本文件。 文件扩展名也可在数组中 `accept` 传递， `.txt` 例如。

若要访问共享文件，请使用与之前一样的请求 `formData` ，并使用 读取 `FileReader` 内容。

```javascript
self.addEventListener('fetch', event => {
    const url = new URL(event.request.url);

    if (event.request.method === 'POST' && url.pathname === '/store-code-snippet') {
        event.respondWith((async () => {
            const data = await event.request.formData();

            const filename = data.get('title');
            const file = data.get('textFile');

            const reader = new FileReader();
            reader.onload = function(e) {
                const textContent = e.target.result;

                // Do something with the textContent here.

            };
            reader.readAsText(file);

            return Response.redirect('/snippet-stored-success', 303);
        })());
    }
});
```


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [与使用 Web 共享 API 的操作系统共享 UI 集成][ShareWebDev]
*  [使用 Web 共享目标 API 接收共享数据][ShareTargetWebDev]


<!-- ====================================================================== -->
<!-- links -->
[MDNWebShareAPI]: https://developer.mozilla.org/docs/Web/API/Web_Share_API "Web 共享 API - Web API |MDN"
[MDNFileInterface]: https://developer.mozilla.org/docs/Web/API/File "文件 - Web API |MDN"
[W3CWebShareTargetAPI]: https://w3c.github.io/web-share-target/level-2/ "Web 共享目标 API |W3C"
[BackgroundSync]: ./background-syncs.md "在后台服务器中同步|Microsoft Docs"
[ShareWebDev]: https://web.dev/web-share/ "与 OS 共享 UI 与 Web 共享 API 集成|web.dev"
[ShareTargetWebDev]: https://web.dev/web-share-target/ "使用 Web 共享目标 API 服务接收|web.dev"
[DemoDevToolsTips]: https://devtoolstips.org/ "DevTools 使用技巧"
[DemoDevToolsTipsGitHub]: https://github.com/captainbrosset/devtools-tips/ "DevTools 使用技巧 |GitHub"
[DemoDevToolsTipsShareFunction]: https://github.com/captainbrosset/devtools-tips/blob/main/src/assets/share.js#L38 "DevTools 使用技巧 |GitHub"
