# <a name="microsoft-edge-developer-documentation"></a>Microsoft Edge 开发人员文档


<!-- ====================================================================== -->
## <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 开源行为准则

请参阅 [Microsoft 开源行为准则](CODE_OF_CONDUCT.md)。


<!-- ====================================================================== -->
## <a name="legal-notices"></a>法律声明

Microsoft 和任何参与者根据 [Creative Commons Attribution 4.0 国际公共许可证](https://creativecommons.org/licenses/by/4.0/legalcode) 向你授予 Microsoft 文档和其他内容的许可证， (查看 [LICENSE](LICENSE)) ，并向你授予 [MIT 许可证](https://opensource.org/licenses/MIT) 下存储库中任何代码的许可证 (请参阅 [LICENSE-CODE](LICENSE-CODE)) 。

本文档中引用的 Microsoft、Windows、Microsoft Azure 和/或其他 Microsoft 产品和服务是 Microsoft 在美国和/或其他国际/地区的商标或注册商标。  此项目的许可证并未授予你使用任何 Microsoft 名称、徽标或商标的权利。  Microsoft 通用商标准则可在 [Microsoft 商标和品牌指南](https://go.microsoft.com/fwlink/?LinkID=254653)中找到。

可在以下位置 [https://privacy.microsoft.com](https://privacy.microsoft.com)找到隐私信息。

Microsoft 及任何创作人保留所有其他权利（无论是其各自的版权、专利或商标），无论是通过默示、禁止否认的方式还是以其他方式。


<!-- ====================================================================== -->
## <a name="contributing"></a>贡献

此存储库 `edge-developer`是 Microsoft Edge 开发人员文档的源 Markdown 文件的存储库。  生成的呈现文档托管在 [Microsoft Edge 文档](https://docs.microsoft.com/microsoft-edge/developer/)中。  此存储库还包括 Microsoft Edge Enterprise 文档的中心页面和 Microsoft Edge 开发人员文档。  Microsoft Edge Enterprise 文档的源文件不在此存储库中，而是在 [Edge-Enterprise](https://github.com/MicrosoftDocs/Edge-Enterprise) 存储库中。

如果想要包括新的覆盖范围或提供反馈，请考虑 [参与](CONTRIBUTING.md)。  可以编辑现有内容、添加新内容或报告新 [问题](https://github.com/MicrosoftDocs/edge-developer/issues)。  Microsoft Edge 团队会查看建议，并努力将建议合并到文档中。

有关 Microsoft Edge 中 Web 平台功能的最新实现状态和未来计划，请参阅 [Microsoft Edge 平台状态](https://developer.microsoft.com/microsoft-edge/status)。 有关用于填充上述状态站点的数据，请参阅 [https://github.com/MicrosoftEdge/Status](https://github.com/MicrosoftEdge/Status)。


### <a name="file-names-and-directories"></a>文件名和目录

*  在将网页添加 (作为 .md 文件) 实现的文章时，必须为 [toc.yml](microsoft-edge/toc.yml) 中的新网页添加一个条目，以便文章显示在目录中。

*  目录可以包含更多目录或 `readme.md` 文件。

*  文件夹/目录名称是短划线分隔的 (例如， `f12-tools`) 和小写。  目录用于网站上的 `docs.microsoft.com` URL。  避免使用下划线、PascalCase 或 camelCase。


<!-- ====================================================================== -->
## <a name="markdown-tagging"></a>Markdown 标记

* [基本写入和格式化语法](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) - GitHub 文档中的 _GitHub_ Flavored Markdown。
* [Docs Markdown 参考](https://docs.microsoft.com/contribute/markdown-reference) - 在 _Docs 参与者指南_中。


### <a name="images"></a>图片

```md
![Alt text](articlefilename-images/image-file-name.png)
```

此存储库使用 Markdown 映像标记。  请参阅 [图像](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#images)。
