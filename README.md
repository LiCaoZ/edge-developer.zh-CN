# <a name="microsoft-edge-developer-documentation"></a>Microsoft Edge 开发人员文档


<!-- ====================================================================== -->
## <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 开放源代码行为准则

请参阅 [Microsoft 开放源代码行为准则](CODE_OF_CONDUCT.md)。


<!-- ====================================================================== -->
## <a name="legal-notices"></a>法律声明

Microsoft 和任何参与者根据[Creative Commons Attribution 4.0 国际](https://creativecommons.org/licenses/by/4.0/legalcode)公共许可证 (授予你 Microsoft 文档和该存储库中其他内容的许可证 (请参阅[LICENSE](./LICENSE)) ，并授予你 MIT 许可证 (下存储库中任何代码[](https://opensource.org/licenses/MIT)的许可证 (请参阅[LICENSE-CODE](./LICENSE-CODE)) 。

本文档中引用的 Microsoft、Windows、Microsoft Azure 和/或其他 Microsoft 产品和服务是 Microsoft 在美国和/或其他国际/地区的商标或注册商标。  此项目的许可证并未授予你使用任何 Microsoft 名称、徽标或商标的权利。  可以在 上找到 Microsoft 一般商标准则 [https://go.microsoft.com/fwlink/?LinkID=254653](https://go.microsoft.com/fwlink/?LinkID=254653) 。

隐私信息位于 [https://privacy.microsoft.com](https://privacy.microsoft.com) 。

Microsoft 及任何创作人保留所有其他权利（无论是其各自的版权、专利或商标），无论是通过默示、禁止否认的方式还是以其他方式。


<!-- ====================================================================== -->
## <a name="contributing"></a>参与

此存储库是开发人员 `edge-developer` 文档的源 Markdown 文件的Microsoft Edge存储库。  生成的呈现文档托管在文档[Microsoft Edge中](https://docs.microsoft.com/microsoft-edge/developer/)。  此存储库还包括开发人员文档和开发人员Microsoft Edge Enterprise中心Microsoft Edge页面。  文档文档的源文件Microsoft Edge Enterprise此存储库，但位于[Edge-Enterprise](https://github.com/MicrosoftDocs/Edge-Enterprise)文件中。

如果你想要包含新的覆盖范围或提供反馈，请考虑 [提供](CONTRIBUTING.md)。  您可以编辑现有内容、添加新内容或报告新 [问题](https://github.com/MicrosoftDocs/edge-developer/issues)。  工作组Microsoft Edge查看您的建议，并努力将这些建议纳入文档。

查找"状态"网页 [的数据](https://developer.microsoft.com/microsoft-edge/status) ，位置为 [https://github.com/MicrosoftEdge/Status](https://github.com/MicrosoftEdge/Status) ：。  网页 `Status` 提供了 Web 平台功能的最新实现状态和未来Microsoft Edge。

### <a name="file-names-and-directories"></a>文件名和目录

*   在添加网页 (作为 .md 文件) 实现的文章时，必须在 [toc.yml](./microsoft-edge/toc.yml)中添加新网页的条目，文章必须显示在目录下。
*   目录可以包含更多目录或 `readme.md` 文件。
*   文件夹/目录名称是短划线 (例如，) `f12-tools` 小写。  目录用于网站的 `docs.microsoft.com` URL。  避免使用下划线、PascalCase 或 camelCase。


<!-- ====================================================================== -->
## <a name="markdown-tagging"></a>Markdown 标记

此存储库使用简单的 Markdown 标记，根据文档参与者指南 docs.microsoft.com 标准 _标记_。

*  [Docs Markdown 参考](https://docs.microsoft.com/contribute/markdown-reference) - 在 _文档参与者指南中_。
*  [在文档GitHub](https://docs.github.com/en/github/writing-on-github) - GitHub的 Markdown 上GitHub_编写_。


### <a name="lists"></a>列表

这些其他文本元素具有可用的样式：

*   无序列表
*   具有常规项目符号
    *   您还可以嵌套项目符号。
    *   项目符号列表应具有多个条目。
*   标准排列

1.  已排序列表。
1.  使用常规的西文编号。
1.  应仅在列表确实具有顺序时使用。

请参阅 [文档 (指南中的 ](https://docs.microsoft.com/en-us/contribute/markdown-reference#lists-numbered-bulleted-checklist) 列表) 编号、项目符号、清单 _列表_。


### <a name="links"></a>Links

请参阅 [文档参与者指南](https://docs.microsoft.com/en-us/contribute/how-to-write-links) 中的使用 _文档中的链接_。


### <a name="formatting-code-blocks"></a>格式化代码块

若要在语句中设置内嵌代码的格式（如 ，请用 `functionName` 反号包装代码）。  Backtick 是一个倾斜的单引号，通常位于键盘的左上角。

也可以显示多行代码块。  以下代码段是一个 CSS 示例。

```css
body {
    background: #fff;
}
```

用于语法颜色的有效编码语言包括以下内容等。  其他值通常是安全的;unknown "slug" 字符串的呈现方式与键入它们的方式相同。

| Slug | 呈现为 |
|---|---|
| html | HTML |
| css | CSS |
| javascript | JavaScript | 
| typescript | TypeScript |
| json | JSON |
| cpp | C++ |
| 主机 | 控制台 |

例如，键入三个 backticks，然后键入"css"slug。

请参阅 [文档参与者指南中的](https://docs.microsoft.com/en-us/contribute/code-in-docs) 如何将代码包括在 _文档内_。


### <a name="tables"></a>表

| 你可以 | 使用列标题 | 表上的 |
|:-- |:--- |:--- |
| 左对齐 | 除非# | 456 |
| 文本值 | 更多文本 | $0.00 |

请参阅 [文档](https://docs.microsoft.com/en-us/contribute/markdown-reference#tables) 参与者 _指南中的表_。


### <a name="notes-alerts"></a>警报 (注释) 

请谨慎使用警报，如"便笺"。  这些块旨在突出显示"不要错过"信息。

提供以下版本的警报。  将纯文本替换为您自己的内容。

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

![注意模式。](./media/notes.png)

对于多行 blockquote 笔记，在每个注释行前面 () 一个大于或大于 100 `>` 个字符的字符：

```md
> This is a line in a blockquote.  It's ok for it to be very long; it will wrap.
> *  This is a list item.
> *  This is another list item.
>
> This is another line in a blockquote.
```

请参阅[文档 (](https://docs.microsoft.com/en-us/contribute/markdown-reference#alerts-note-tip-important-caution-warning)指南中的警报、注释、提示、重要、) _警告和警告。_


### <a name="images"></a>图片

图像应存储在 `media` 目录中。  使用下面的三个冒号图像标记引用具有相对于 Markdown 文件的相对路径的图像：

```md
:::image type="content" source="./media/notes.png" alt-text="Describe what's shown in the image." lightbox="./media/notes.png":::
```

请参阅 [文档](https://docs.microsoft.com/en-us/contribute/markdown-reference#images) 参与者 _指南中的图像_。


---

### <a name="horizontal-rules-divider-lines"></a>水平规则 (分隔线) 

若要创建水平规则，请单独在一行上使用三个连字符; `---`.  请慎用水平规则。  避免在标题正上方或下方使用水平规则;一些标题已对可视化层次结构使用线条样式。
