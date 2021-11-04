---
description: 安装和使用 webhint 扩展Visual Studio Code。
title: webhint 扩展Visual Studio Code
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/24/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， Web 开发， vs code， visual studio code， webhint
ms.openlocfilehash: 5cd40a4c9c7a7b91893853064bd8fc56d98e34f9
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12156996"
---
# <a name="the-webhint-extension-for-visual-studio-code"></a>webhint 扩展Visual Studio Code

使用[Webhint（](https://webhint.io)一种可自定义的 Lint 工具）可改进网站的辅助功能、性能、跨浏览器PWA兼容性和安全性。  它会检查代码的最佳实践和常见错误。 此开放源代码项目最初由 Microsoft Edge 开发，现在是[OpenJS Foundation 的一部分](https://openjsf.org)。  Microsoft Edge团队将继续与社区中的 Web 开发人员一起为 webhint 做贡献。

通过添加 webhint 扩展以识别并修复 HTML、CSS、JavaScript、TypeScript 等中的问题Visual Studio Code。  提示显示为内联下划线，并汇总在"问题 **"** 窗格中。

:::image type="complex" source="./media/webhint-extension.png" alt-text="webhint 扩展Visual Studio Code":::
   webhint 扩展Visual Studio Code
:::image-end:::


<!-- ====================================================================== -->
## <a name="installing-webhint"></a>安装 Webhint

若要从 webhint 安装 webhint 扩展Visual Studio Code，请导航到[webhint extension for Visual Studio Code](index.md#the-webhint-extension-for-visual-studio-code)。 <!-- in the article _Visual Studio Code overview_. -->  或者，也可以安装[Webhint 扩展，Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=webhint.vscode-webhint)应用商店Visual Studio Webhint。


<!-- ====================================================================== -->
## <a name="configuring-webhint-in-visual-studio-code"></a>在网站中配置 webhint Visual Studio Code

此扩展使用默认配置[json](https://github.com/webhintio/hint/blob/master/packages/configuration-development/index.json)文件，该文件可激活 HTML、CSS、模板化系统 (JSX/TSX、Angular 等) 、JavaScript/TypeScript 等的提示和分析程序。

```json
{
    "connector": "local",
    "extends": [
        "accessibility",
        "progressive-web-apps"
    ],
    "formatters": [
        "html",
        "summary"
    ],
    "hints": [
        "apple-touch-icons",
        "button-type",
        "compat-api/css",
        "compat-api/html",
        "create-element-svg",
        "css-prefix-order",
        "disown-opener",
        "highest-available-document-mode",
        "manifest-exists",
        "meta-charset-utf-8",
        "meta-viewport",
        "no-bom",
        "no-protocol-relative-urls",
        "scoped-svg-styles",
        "sri",
        "typescript-config/consistent-casing",
        "typescript-config/import-helpers",
        "typescript-config/is-valid",
        "typescript-config/no-comments",
        "typescript-config/strict",
        "typescript-config/target"
    ],
    "hintsTimeout": 10000,
    "parsers": [
        "babel-config",
        "css",
        "html",
        "javascript",
        "jsx",
        "less",
        "sass",
        "typescript",
        "typescript-config",
        "webpack-config"
    ]
}
```

如果你希望对激活的提示和分析程序进行更多控制，请创建一个本地 `.hintrc` 文件来配置 Webhint。  有关特定提示输出的帮助，请导航到 [Webhint 用户指南](https://webhint.io/docs/user-guide/configuring-webhint/summary)。


<!-- ====================================================================== -->
## <a name="getting-in-touch-with-the-webhint-team"></a>与 Webhint 团队联系

通过向[Webhintio/hint 存储库提交问题来发送](https://github.com/webhintio/hint)反馈。 [](https://github.com/webhintio/hint/issues/new)

若要参与扩展，请 [导航到存储库](https://github.com/webhintio/hint/blob/master/packages/extension-vscode/CONTRIBUTING.md) 的"参与 `webhintio/hint` "。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [辅助功能](/microsoft-edge/accessibility)
*  [Visual Studio Code](/microsoft-edge/visual-studio-code/index)
