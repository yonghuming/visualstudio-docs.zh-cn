---
title: "使用针对 Visual Studio 的 R 工具的代码片段 | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bf4f87-e276-40cd-bc17-3dfb47ef1870
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 033a06b276b8a31e6c69b0eff68ee3f76dda1042
ms.contentlocale: zh-cn
ms.lasthandoff: 05/12/2017

---

# <a name="code-snippets"></a>代码片段

Visual Studio 中的代码片段提供了一些快捷方式，可用于快速插入任意长度的代码块，有助于避免反复键入相似的代码。 针对 Visual Studio 的 R 工具 (RTVS) 向 Visual Studio 的集合添加了许多有用的 R 代码片段。

要插入代码片段，请键入代码片段的缩写名称（支持 IntelliSense），然后按 Tab 插入。

一些简单示例如下：

- 键入 `=` 然后按 Tab，RTVS 会将其展开为 `<-` 赋值运算符。
- 键入 `>` 然后按 Tab，RTVS 会将其展开为 `%>%` 管道运算符。

代码片段的用途远不只是拼写完字符。 例如，它们可以帮助你免于记忆复杂函数调用中的参数名称，例如这个通过 `read.csv` 函数来读取 CSV 文件的代码片段：

![使用代码片段插入对 read.csv 的调用的动画](media/code-snippet-expansion.gif)

在这种情况下，当键入 `readc` 时，IntelliSense 将显示一个完成列表。 在下拉菜单中选择该完成项，按 Tab 选择 `readc`，然后再次按 Tab 展开代码片段。 （因此，通常认为展开代码片段是“键入代码片段并按 Tab 两次”）。 在大多数情况下，第一次按 Tab 完成 IntelliSense 选择，第二次按 Tab 触发展开。

要查看所有可用的代码片段，请打开“工具”>“代码片段管理器...”对话框（Ctrl+K、B），并为“语言”选择“R”。 展开组并选择单独的代码片段，查看说明和快捷方式文本：

![R 的代码片段对话框](media/code-snippet-dialog.png)

要创建自定义代码片段，请按照[演练：创建代码片段](../ide/walkthrough-creating-a-code-snippet.md)中的说明进行操作。 最终，代码片段只是一个 XML 文件。 例如，以下代码片段用于管道操作（快捷方式 `>`）

请注意，代码片段只是一个 XML 文件；以下是用于管道运算符的代码片段：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

用于所有代码片段的 XML 文件是随 RTVS 一起安装的；“代码片段管理器”中的“位置”字段提供了相关路径。 也可以在 [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets) 下 GitHub 的 RTVS 源代码中找到它们。

