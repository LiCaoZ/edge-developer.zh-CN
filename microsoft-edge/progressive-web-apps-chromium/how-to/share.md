---
title: 与其他应用共享内容
description: 如何与其他应用共享来自PWA，并接受来自其他应用的共享内容。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
ms.date: 09/27/2021
ms.openlocfilehash: 2c314ef4118175f878b2eb82f049688f0f5b05b0
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431989"
---
# <a name="share-content-with-other-apps"></a>与其他应用共享内容

在应用之间共享内容由移动设备所热门，其中操作文件或复制内容不如在桌面操作系统上直观。  例如，在移动电话上，通常通过发送短信与好友共享图像。  但是，共享内容不会保留给移动设备;此外，在应用程序上的应用之间Windows共享。

共享内容有两个方向，这两个方向都可以由渐进式 Web 应用 (PWA) ：

| Direction | 说明 |
|---|---|
| 共享内容 | 若要共享内容，PWA生成 (内容，例如文本、链接或) 将共享内容上线到操作系统。  操作系统允许用户决定要使用哪个应用接收该内容。 |
| 接收共享内容 | 若要接收内容，PWA用作内容目标。  该PWA在操作系统中注册为内容共享目标。 |

注册为共享目标的 PWA 感觉本地已集成到操作系统中，并且更吸引用户。


<!-- ====================================================================== -->
## <a name="sharing-content"></a>共享内容

PWA 可以使用 [Web 共享 API](https://developer.mozilla.org/docs/Web/API/Web_Share_API) 触发显示操作系统共享对话框。

> [!NOTE]
> Web 共享仅适用于通过 HTTPS (服务的网站，PBA) 的情况，并且只能调用它以响应用户操作。

若要共享链接、文本或文件等内容，请使用 `navigator.share` 函数，如下所示。  函数 `navigator.share` 接受至少应具有以下属性之一的对象：

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

在以上代码中，我们首先通过测试是否已定义来检查浏览器 `navigator.share` 是否支持 Web 共享。  该 `navigator.share` 函数返回 [一个 Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) 对象，该对象在共享成功时解析，在发生错误时拒绝。

因为此处使用了 Promise，所以上述代码可以重写为函数 `async` ，如下所示：

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

在Windows，上述代码将触发共享对话框，允许用户选取应用以接收共享内容。  共享对话框如下所示：

:::image type="content" source="../media/windows-share-dialog.png" alt-text="&quot;共享&quot;对话框Windows。":::

用户选择应用以接收共享内容后，由该应用以任何方式处理它。  例如，电子邮件应用可能将 用作 `title` 电子邮件主题，并使用 作为 `text` 电子邮件正文。


### <a name="sharing-files"></a>共享文件

函数 `navigator.share` 还接受用于与其他 `files` 应用共享文件的数组。

在共享文件之前，测试共享文件是否受浏览器支持，这一点很重要。 若要检查是否支持共享文件，请使用 `navigator.canShare` 函数：

```javascript
function shareSomeFiles(files) {
  if (navigator.canShare && navigator.canShare({files})) {
    console.log('Sharing files is supported');
  } else {
    console.error('Sharing files is not supported');
  }
}
```

共享 `files` 对象成员必须是对象数组 `File` 。 详细了解 File [接口](https://developer.mozilla.org/docs/Web/API/File)。

构造对象的一 `File` 种方式是：
1. 首先，使用 `fetch` API 请求资源。
1. 然后，使用返回的响应创建新的 `File`。

此方法如下所示。

```javascript
async function getImageFileFromURL(imageURL, title) {
  const response = await fetch(imageURL);
  const blob = await response.blob();
  return new File([blob], title, {type: blob.type});
}
```

在以上代码中：
1. 函数 `getImageFileFromURL` 使用 URL 获取图像。
1. 该 `response.blob()` 函数将图像转换为二进制大型对象 (BLOB) 。
1. 代码使用 `File` BLOB 创建对象。


### <a name="demo-of-sharing-content"></a>共享内容的演示

[DevTools 使用技巧](https://devtoolstips.org/)是一PWA使用 函数`navigator.share`共享文本和链接的开发人员。

若要测试功能：：

1. 转到 [DevTools 使用技巧](https://devtoolstips.org/)。
2. 选择提示。
3. 单击 **"共享提示"**。

将显示**Windows共享"** 对话框。  用户选取要共享内容的应用：

:::image type="content" source="../media/devtools-tips-share.png" alt-text="&quot;Windows共享&quot;对话框允许用户选取应该接收共享内容的应用。":::

您可以在该代码中[找到GitHub](https://github.com/captainbrosset/devtools-tips/)。  应用程序使用应用程序源文件中的 Web [share.js](https://github.com/captainbrosset/devtools-tips/blob/main/src/assets/share.js#L38) API。


<!-- ====================================================================== -->
## <a name="receiving-shared-content"></a>接收共享内容

通过使用 [Web 共享目标](https://w3c.github.io/web-share-target/level-2/) API，PWA注册为在系统共享对话框中显示为应用。  然后PWA Web 共享目标 API 处理来自其他应用的共享内容。

> [!NOTE]
> 只有已安装的 PWA 才能注册为共享目标。

### <a name="register-as-a-target"></a>注册为目标

若要接收共享内容，首先要将你的PWA注册为共享目标。  若要注册，请使用清单 `share_target` 成员。  安装应用后，操作系统会 `share_target` 使用该成员将你的应用包括在系统共享对话框中。  操作系统知道在用户选取你的应用时要执行哪些操作来共享内容。

成员 `share_target` 必须包含系统将共享内容传递到应用的必要信息。  请考虑以下清单代码：

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

当用户选择你的应用作为共享内容的目标时，PWA启动。  对 `GET` 属性指定的 URL 进行 `action` HTTP 请求。  共享数据作为 、 `title`和 `text`查询参数 `url` 传递。  将提出以下请求： `/handle-shared-content/?title=shared title&text=shared text&url=shared url`。

如果您有使用其他查询参数名称的现有代码，您可以将 `title`默认 、 `text`和 `url` 查询参数映射到其他名称。  在下面的示例中，、 `title`和 `text``url` 查询参数将映射到 `subject`、 `body`和 `address`：

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

若要处理在代码代码中通过 GET 请求PWA的数据，`URL`请使用构造函数提取查询参数：

```javascript
window.addEventListener('DOMContentLoaded', () => {
    console url = new URL(window.location);

    const sharedTitle = url.searchParams.get('title');
    const sharedText = url.searchParams.get('text');
    const sharedUrl = url.searchParams.get('url');
});
```

### <a name="handle-post-shared-data"></a>处理 POST 共享数据

如果共享数据旨在 `POST` 以任何方式更改你的应用，例如通过更新应用中存储的一些内容，则必须使用 方法并使用 定义编码类型 `enctype`：

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

HTTP `POST` 请求包含编码为 的共享数据 `multipart/form-data`。  您可以使用服务器端代码在 HTTP 服务器上访问此数据，但当用户处于脱机状态时，这不起作用。  为了提供更好的体验，可以使用事件 `fetch` 侦听器访问服务工作器中的数据，如下所示：

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

在以上代码中：

1. 服务工作线程截获 `POST` 请求。

1. 以某种方式使用数据 (例如，将内容存储在本地) 。

1. 将用户重定向到成功页面。  这样，即使网络关闭，应用也可以运行。  应用可以选择仅在本地存储内容，也可以选择稍后在连接还原时（例如，使用后台同步 (将 [内容发送到) ](background-syncs.md) 。

### <a name="handle-shared-files"></a>处理共享文件

应用还可以处理共享文件。 若要在文件中处理PWA，必须使用 `POST` 方法和编码`multipart/form-data`类型。 此外，你必须声明你的应用可以处理的文件类型。

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
                    "accept": ["text/plain", "text/html", "text/css", 
                               "text/javascript"]
                }
            ]
        }
    }
}
```

上述清单代码告知系统你的应用可以接受各种 MIME 类型的文本文件。  还可以在数组中传递`.txt``accept`文件扩展名（如 ）。

若要访问共享文件，请使用与之前一 `formData` 样的请求，并使用 读取 `FileReader` 内容，如下所示：

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

*  [与使用 Web 共享 API 的操作系统共享 UI 集成](https://web.dev/web-share/)
*  [使用 Web 共享目标 API 接收共享数据](https://web.dev/web-share-target/)
