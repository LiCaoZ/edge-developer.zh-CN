---
title: 通过将源映射发布到Azure Artifacts符号服务器来安全地调试原始代码
description: 了解如何将源映射发布到Azure Artifacts符号服务器，以便在 DevTools 中安全调试原始源代码。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 03/02/2022
ms.openlocfilehash: cf60d4dbf7edc7e28d51c0d80753aa77f3b2244b
ms.sourcegitcommit: d79f328b1dd650be153ba9edac99f6a5c371aaeb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/15/2022
ms.locfileid: "12478453"
---
# <a name="securely-debug-original-code-by-publishing-source-maps-to-the-azure-artifacts-symbol-server"></a>通过将源映射发布到Azure Artifacts符号服务器来安全地调试原始代码

安全地<!-- add sentence to define "securely", what are we making not happen?  what's the UX/end-result motivation for "securely"? --> 查看并使用 DevTools 中的原始开发源代码，而不是 Web 服务器返回的编译、细化和捆绑生产代码，使用由Azure Artifacts符号服务器提供的源映射。

将源映射直接发布到 Web 服务器将使原始源代码公开可见。  若要避免使原始源代码公开可见，请将源映射发布到Azure Artifacts符号服务器。  通过此方法，可以在调试生产网站时在 DevTools 中使用源映射，而无需将源映射发布到 Web 服务器。

源映射将已编译的生产代码映射到原始开发源文件。 然后，在 DevTools 中，可以看到并使用熟悉的开发源文件，而不是编译的代码。 若要详细了解源映射和使用 DevTools 中的源映射，请参阅 [将已处理代码映射到原始源代码，以便进行调试](source-maps.md)。


<!-- ====================================================================== -->
## <a name="concepts"></a>概念

必须在Azure Artifacts符号服务器上为源映射编制索引，以便在调试生产网站时，源映射可供 DevTools 使用。

为此，请在 `x_microsoft_symbol_client_key` 编译时将字符串属性添加到源映射。  此属性包含相应原始源文件的 [256 位 SHA-2 哈希](https://en.wikipedia.org/wiki/SHA-2) 的小写十六进制值。

然后，DevTools 能够计算每个已编译文件的此哈希，并使用哈希从Azure Artifacts符号服务器检索正确的源映射。  为了安全地检索源映射，DevTools 使用你提供的个人访问令牌连接到Azure Artifacts符号服务器。


<!-- ====================================================================== -->
## <a name="step-1-generate-a-personal-access-token-for-azure-devops"></a>步骤 1：为Azure DevOps生成个人访问令牌

将源映射发布到Azure Artifacts符号服务器需要[个人访问令牌](/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate) (或 PAT) 。 编译代码和发布源映射时，生成系统将使用此 PAT。

若要在Azure DevOps中生成 PAT：

1. 通过转到`https://dev.azure.com/{yourorganization}`Azure DevOps组织登录。

1. 在Azure DevOps中，转到 **User settingsPersonal** >  **访问令牌**：
    
   ![Azure DevOps中的“用户设置”菜单，其中包含“个人访问令牌”命令。](images/ado-pat-settings.png)

   将显示 **“个人访问令牌”** 页：

   ![Azure DevOps中的“个人访问令牌”页。](images/ado-pat-page.png)

1. 单击 **“新建令牌**”。  “ **创建新的个人访问令牌** ”对话框随即打开：

   ![“创建新的个人访问令牌”对话框，其中选择了符号的“读取&写入”范围。](images/ado-pat-config-write.png)

1. 在 **“名称”** 文本框中，输入 PAT 的名称，例如“发布源映射”。

1. 在 **“过期”** 部分中，输入 PAT 的到期日期。

1. 在“ **作用域”** 部分中，单击 **“显示所有范围** ”以展开该部分。

1. 向下滚动到 **“符号”** 部分，然后选择 **“读取&写** 入复选框。

1. 单击 **“创建”** 按钮。  **成功！** 将显示对话框：

   ![“成功！” 包含要复制的 PAT 的对话框。](images/ado-pat-success-copy-clipboard.png)

1. 单击 **“复制到剪贴板** ”按钮以复制 PAT。  请确保复制令牌并将其存储在安全位置。 为了安全起见，不会再显示它。

若要了解有关 PAT 的详细信息，请参阅 [“使用个人访问令牌](/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate)”。


<!-- ====================================================================== -->
## <a name="step-2-compute-the-sha-256-hash-of-your-script-and-append-it-to-your-source-maps"></a>步骤 2：计算脚本的 SHA-256 哈希并将其追加到源映射

在应用程序生成过程的最后一步中，对于要发布的每个源映射，应计算源映射对应到的 JavaScript 文件的 SHA-256 哈希，并通过字符串属性将其追加到源映射 `x_microsoft_symbol_client_key` 。

生成系统因应用程序而异，因此没有明确的单一方法可以应用。 但下面是一个 [示例 Webpack 5 插件](https://webpack.js.org/)，如果使用它，可以将其添加到 Webpack 配置中：

```js
// file: webpack.plugin-symbols.js
// Copyright (C) Microsoft Corporation. All rights reserved.
// Licensed under the BSD 3-clause license.

const crypto = require('crypto');
const fs = require('fs');
const path = require('path');
const process = require('process');

module.exports = class PrepareSourceMapsForSymbolServerPlugin {
  /**
   * @param {import('webpack').Compiler} compiler
   * @returns {void}
   */
  apply(compiler) {
    compiler.hooks.emit.tap('PrepareSourceMapsForSymbolServerPlugin', (compilation) => {
      const files = Object.keys(compilation.assets);
      const sourceMaps = files.filter(v => v.endsWith('.map'));
      const sourceFilesAndMapsNames = sourceMaps.map(mapFileName => {
        const sourceFileName = mapFileName.substring(0, mapFileName.length - 4);
        return {
          sourceFileName,
          mapFileName,
        };
      });
      const sourceFiles = sourceFilesAndMapsNames.map(({ sourceFileName, mapFileName }) => {
        const sourceFile = compilation.assets[sourceFileName];
        const sourceFileBuffer = sourceFile.buffer();
        const hasher = crypto.createHash('sha256');
        hasher.write(sourceFileBuffer);
        const digest = hasher.digest();
        const sourceFileHash = digest.toString('hex');

        const sourceMapAsset = compilation.assets[mapFileName];
        const sourceMapSource = sourceMapAsset.source();
        const sourceMapContents = JSON.parse(sourceMapSource);
        sourceMapContents['x_microsoft_symbol_client_key'] = sourceFileHash;
        const rewrittenSourceMapContents = JSON.stringify(sourceMapContents);
        if (!sourceMapAsset.isBuffer()) {
          // Not a buffer -- write to the _value property
          sourceMapAsset._value = rewrittenSourceMapContents;
        }
        else {
          sourceMapAsset._valueAsBuffer = Buffer.from(rewrittenSourceMapContents, 'utf-8');
        }

        return {
          sourceFileName,
          mapFileName,
          sourceFileHash,
          sourceMapAsset,
        };
      });
    });
  }
};
```

然后，可以将插件添加到 `plugins` 配置文件中的 `webpack.config.js` 节：

```js
const PrepareSourceMapsForSymbolServerPlugin = require('./webpack.plugin-symbols.js');

// ...

module.exports = (env, args) => {
  const mode = process.env.NODE_ENV || (env && env.NODE_ENV) || 'production';
  return {
    devtool: mode === 'production' ? 'hidden-source-map' : 'inline-source-map',
    resolve: {
      modules: [
        path.resolve('./node_modules'),
      ],
    },
    output: {
      publicPath: '/',
      filename: '[name].bundle.js',
      chunkFilename: '[name].chunk.js',
    },
    plugins: [
        // ... other plugins
        new PrepareSourceMapsForSymbolServerPlugin(),
    ]
  });
};
```


<!-- ====================================================================== -->
## <a name="step-3-publish-source-maps-to-the-azure-artifacts-symbol-server"></a>步骤 3：将源映射发布到Azure Artifacts符号服务器


### <a name="publish-source-maps-using-azure-devops-pipelines"></a>使用Azure DevOps Pipelines发布源映射

Azure DevOps随管道生成任务一[`PublishSymbols@2`](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols)起完成。 此任务可用于将源映射发布到Azure Artifacts符号服务器。

请确保将此任务`indexableFileFormats`的参数设置为或`All``SourceMap`设置为 。


### <a name="publish-source-maps-using-symbolexe"></a>使用 >a0/a0> `symbol.exe`

符号服务器团队发布 .NET Core 应用程序，`symbol.exe`[可自动下载](/rest/api/azure/devops/symbol/client/get)。 下载`symbol.exe`后，可以执行命令，将源映射发布到Azure Artifacts符号服务器：

```cmd
symbol publish
        -d {root directory containing your source maps}
        -n {a unique name for this job}
        -s {service URL, such as https://artifacts.dev.azure.com/contoso}
        --patAuthEnvVar {name of environment variable containing a PAT}
        --indexableFileFormats SourceMap
```

请注意， `-n` 该参数必须是唯一的。 重复的作业名称，甚至失败的作业名称，将被拒绝。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [使用Azure Artifacts符号服务器源映射安全地调试原始代码](consume-source-maps-from-azure.md)
* [将已处理的代码映射到原始源代码，以便进行调试](source-maps.md)
