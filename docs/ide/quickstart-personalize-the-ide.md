---
title: "在 Visual Studio 中设置颜色主题和字体 | Microsoft 文档"
ms.custom: 
ms.date: 11/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7adb1ec7badaefceb8430d0fcacd8e54e7404ea7
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2017
---
# <a name="quickstart-personalize-the-visual-studio-ide-and-editor"></a>快速入门：个性化 Visual Studio IDE 和编辑器

在这个 5-10 分钟的快速入门中，我们将在文本编辑器中自定义 Visual Studio 颜色主题和两种文本颜色。

## <a name="set-the-color-theme"></a>设置颜色主题

Visual Studio 2017 的默认颜色主题命名为“蓝色”。 让我们将其更改为“深色”。

1. 在菜单栏上，依次选择“工具”、“选项”。

1. 在“环境”、“常规”选项页上，将选择的“颜色主题”更改为“深色”，然后选择“确定”。

   整个 IDE 的颜色主题更改为“深色”。

   ![深色主题下的 VS](media/quickstart-personalize-dark-theme.png)

> [!TIP]
> 可以通过从 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2017ColorThemeEditor) 中安装“Visual Studio 颜色主题编辑器”来安装其他预定义的主题。 安装此工具后，其他颜色主题将显示在“颜色主题”下拉列表中。

## <a name="change-text-color"></a>更改文本颜色

现在我们将为编辑器自定义一些文本颜色。 首先，让我们打开 XML 文件来查看默认颜色。

1. 在菜单栏上，依次选择“文件”、“新建”“文件...”。

1. 在“新建文件”对话框的“常规”类别中，选择“XML 文件”，然后选择“打开”。

1. 将以下 XML 粘贴到包含 `<?xml version="1.0" encoding="utf-8"?>` 的行的下面。

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   请注意，行号是翠蓝色，xml 属性是浅蓝色。 我们将更改这些项的文本颜色。

   ![XML 文件字体颜色](media/quickstart-personalize-xml-file.png)

1. 若要打开“选项”对话框中，请依次选择菜单栏上的“工具”、“选项”。

1. 在“环境”下，请选择“字体和颜色”类别。

   请注意，“显示以下对象的设置”下的文本是指“文本编辑器”&mdash; 这正是我们所需要的。 你可以展开下拉列表，仅查看可用于自定义字体和文本颜色的位置的扩展列表。

1. 若要更改行号文本的颜色，请在“显示项目”列表中选择“行号”。 在“项目前景色”框中，选择“橄榄色”。

   ![“选项”对话框，“字体和颜色”类别](media/quickstart-personalize-line-number-color.png)

1. 退出对话框中之前，让我们同时更改一下 XML 属性的颜色。 在“显示项”列表中，向下滚动到“XML 属性”，然后选择它。 在“项目前景色”框中，选择“浅绿色”。 选择“确定”以保存我们的选择并关闭对话框。

   行号现在为橄榄色，XML 属性为明亮的浅绿色。 如果打开另一个类型的文件，例如 C++ 或 C# 代码文件，则会发现行号也以橄榄色显示。

   ![使用新的字体颜色的 XML 文件](media/quickstart-personalize-xml-file-new-colors.png)

我们探讨了几种在 Visual Studio 中自定义颜色的方法。 希望你继续深入了解“选项”对话框中的其他自定义选项，以真正使 Visual Studio 为你所用。

## <a name="see-also"></a>请参阅

[快速入门：初步了解 Visual Studio IDE](../ide/quickstart-ide-orientation.md)  
[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)  
[自定义编辑器](../ide/customizing-the-editor.md)  
[Visual Studio IDE 概述](../ide/visual-studio-ide.md)