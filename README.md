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

此存储库`edge-developer`是Microsoft Edge开发人员文档的源 Markdown 文件的存储库。  生成的呈现文档托管在[Microsoft Edge文档](https://docs.microsoft.com/microsoft-edge/developer/)中。  此存储库还包括Microsoft Edge Enterprise文档的中心页面和Microsoft Edge开发人员文档。  Microsoft Edge Enterprise文档的源文件不在此存储库中，而是在 [Edge-Enterprise](https://github.com/MicrosoftDocs/Edge-Enterprise) 存储库中。

如果想要包括新的覆盖范围或提供反馈，请考虑 [参与](CONTRIBUTING.md)。  可以编辑现有内容、添加新内容或报告新 [问题](https://github.com/MicrosoftDocs/edge-developer/issues)。  Microsoft Edge团队会查看建议，并努力将建议合并到文档中。

在以下位置查找[“状态”](https://developer.microsoft.com/microsoft-edge/status)网页的数据。 [https://github.com/MicrosoftEdge/Status](https://github.com/MicrosoftEdge/Status)  该`Status`网页提供Microsoft Edge中 Web 平台功能的最新实现状态和未来计划。

### <a name="file-names-and-directories"></a>文件名和目录

*  在将网页添加 (作为 .md 文件) 实现的文章时，必须为 [toc.yml](microsoft-edge/toc.yml) 中的新网页添加一个条目，以便文章显示在目录中。

*  目录可以包含更多目录或 `readme.md` 文件。

*  文件夹/目录名称是短划线分隔的 (例如， `f12-tools`) 和小写。  目录用于网站上的 `docs.microsoft.com` URL。  避免使用下划线、PascalCase 或 camelCase。


<!-- ====================================================================== -->
## <a name="markdown-tagging"></a>Markdown 标记

此存储库使用简单的 Markdown 标记，这是根据 _Docs 参与者指南_ docs.microsoft.com 的标准。

* [Docs Markdown 参考](https://docs.microsoft.com/contribute/markdown-reference) - 在 _Docs 参与者指南_中。
* [写在GitHub](https://docs.github.com/en/github/writing-on-github) - GitHub调味马克当，在_GitHub文档_。


### <a name="lists"></a>列表

这些其他文本元素具有可用的样式：

*  未排序的列表
*  有常规项目符号
   *  还可以嵌套项目符号。
   *  项目符号列表应有多个条目。
*  标准排列

1. 已排序列表。
1. 使用常规的西式编号。
1. 仅当列表真正具有顺序时才应使用。

请参阅 _Docs 参与者指南_[中的列表 (编号、项目符号、清单) ](https://docs.microsoft.com/contribute/markdown-reference#lists-numbered-bulleted-checklist)。


### <a name="links"></a>Links

请参阅文档中的 _“Docs 参与者指南_”中的[“使用”链接](https://docs.microsoft.com/contribute/how-to-write-links)。


### <a name="formatting-code-blocks"></a>设置代码块格式

若要在句子中设置内联代码的格式（例如 `functionName`，用反斜线包装代码）。  背尖是一个倾斜的单引号，通常位于键盘左上角。

也可以显示多行代码块。  下面的代码片段是一个 CSS 示例。

```css
body {
    background: #fff;
}
```

用于语法着色的有效编码语言包括以下内容等。  其他值通常是安全的;未知的“slug”字符串的呈现方式与键入它们的方式相同。

| 塞 | 呈现为 |
|---|---|
| Html | HTML |
| Css | CSS |
| javascript | JavaScript | 
| typescript | TypeScript |
| Json | JSON |
| Cpp | C++ |
| 主机 | 控制台 |

例如，键入三个后台键，然后键入“css”slug。

请参阅如何在_文档参与者指南_[中包含文档中的代码](https://docs.microsoft.com/contribute/code-in-docs)。


### <a name="tables"></a>表

| 你可以 | 使用列标题 | 在表上 |
|:-- |:--- |:--- |
| 左对齐 | 除非 a# | 456 |
| 文本值 | 更多文本 | $0.00 |

请参阅 _Docs 参与者指南_中的[表](https://docs.microsoft.com/contribute/markdown-reference#tables)。


### <a name="notes-alerts"></a>备注 (警报) 

请谨慎使用警报（如备注）。  这些块旨在突出显示“不要错过”信息。

以下版本的警报可用。  将纯文本替换为你自己的内容。

```md
> [!NOTE]
> Information the user should notice even if skimming.
```

```md
> [!TIP]
> Optional information to help a user be more successful.
```

```md
> [!IMPORTANT]
> Essential information required for user success.
```

```md
> [!CAUTION]
> Negative potential consequences of an action.
```

```md
> [!WARNING]
> Dangerous certain consequences of an action.
```

![注意模式。](media/notes.png)

对于多行块引注，请在备注的每行前面使用大于 (`>`) 字符：

```md
> This is a line in a blockquote.  It's ok for it to be very long; it will wrap.
> *  This is a list item.
> *  This is another list item.
>
> This is another line in a blockquote.
```

请参阅 _Docs 参与者指南_[中的警报 (注意、提示、重要、警告、警告) ](https://docs.microsoft.com/contribute/markdown-reference#alerts-note-tip-important-caution-warning)。


### <a name="images"></a>图片

映像应存储在目录中 `media` 。  使用以下三重冒号图像标记，使用相对于 Markdown 文件的相对路径引用图像：

```md
:::image type="content" source="./media/notes.png" alt-text="Describe what's shown in the image." lightbox="./media/notes.png":::
```

请参阅 _Docs 参与者指南_中的[图像](https://docs.microsoft.com/contribute/markdown-reference#images)。


---

### <a name="horizontal-rules-divider-lines"></a>水平规则 (分隔线) 

若要创建水平规则，请在行上单独使用三个连字符： `---`.  在此存储库中，很少使用这些存储库;它们在 API 函数部分之间使用。

此存储库中的几个文件中使用了等效的 `* * *` Markdown 标记，用于标识一组选项卡的末尾，以便为每个选项卡生成一种编程语言的文档。
