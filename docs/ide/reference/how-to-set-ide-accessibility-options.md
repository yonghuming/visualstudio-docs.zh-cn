---
title: "如何：设置 IDE 辅助功能选项 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "辅助功能 [Visual Studio]"
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：设置 IDE 辅助功能选项
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 包含一些辅助性功能，可使有视觉障碍的人更方便地阅读，并使行动不便的人更方便地书写。  这些功能包括更改编辑器中文本的大小和颜色，更改工具栏上文本和按钮的大小，以及方法和参数的自动完成等。  
  
 此外，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支持 Dvorak 键盘布局，这些布局使最频繁键入的字符使用起来更为方便。  您还可以自定义可在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中使用的默认快捷键。  有关详细信息，请参阅 [标识并自定义键盘快捷键](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 编辑器、对话框和工具窗口  
 默认情况下，对话框和工具窗口。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用字体大小和颜色和操作系统相同。  IDE、对话框、工具栏和工具窗口的框架的颜色设置基于配色方案：光源或暗。  您可以更改在 [“选项”对话框 \-\>“环境”\-\>“常规”](../../ide/reference/general-environment-options-dialog-box.md)的当前颜色主题。  
  
 还可以显示在编辑器的"代码"视图的弹出窗口。  这些窗口可以提示您当前对象和参数的可用成员的完成函数或语句。  如果您有困难键入，这些窗口会很有用。  但是，它们的确干扰焦点在代码编辑器中，可能有问题的某些用户。  可以通过在中打开选项"对话框并清除 **自动列出成员** 关闭这些窗口和 **参数信息** 在 **文本编辑器**，**所有语言**，**常规** 页在 **选项** 对话框。  有关详细信息，请参阅 [How to: Set General Editor Options](http://msdn.microsoft.com/zh-cn/704e4a7b-2162-4bed-8a47-f4f6ffec98c2)。  
  
 可以在集成开发环境 \(IDE\) 中重新排列窗口，以便更好地适合工作。  可停靠，浮点数，隐藏或自动隐藏每个工具窗口。  
  
 有关以下内容的详细信息如何更改 windows 窗体，请参见 [自定义窗口布局](../../ide/customizing-window-layouts-in-visual-studio.md)。  
  
### 更改文本的大小  
 您可以更改基于文本的工具窗口的设置，如**“工具”**对话框中**“环境”**选项的**“字体和颜色”**窗格中的**“命令”**窗口、**“即时”**窗口和**“输出”**窗口。  在**“显示其设置”**下拉列表中选择**“\[全部文本工具窗口\]”**后，默认设置会在**“项前景”**和**“项背景”**下拉列表中作为**“默认值”**列出。  您也可以为编辑器中文本的显示方式更改设置。  
  
##### 更改基于文本的工具窗口和编辑器中文本的大小  
  
1.  从**“工具”**菜单中选择**“选项”**。  
  
2.  在**“环境”**文件夹上选择**“字体和颜色”**。  
  
3.  在**“显示其设置”**下拉菜单中选择一个选项。  
  
     若要更改编辑器中文本的字体大小，请选择**“文本编辑器”**。  
  
     若要更改基于文本的工具窗口中文本的字体大小，请选择**“\[全部文本工具窗口\]”**。  
  
     若要更改编辑器中工具提示文本的字体大小，请选择**“编辑器工具提示”**。  
  
     若要更改语句结束弹出消息中文本的字体大小，请选择**“语句结束”**。  
  
4.  从**“显示项”**中选择**“纯文本”**。  
  
5.  在**“字体”**中，选择一个新字体类型。  
  
6.  在**“大小”**中，选择新字体大小。  
  
    > [!NOTE]
    >  若要为基于文本的工具窗口和编辑器重置文本的大小，请选择**“使用默认值”**。  
  
7.  选择**“确定”**。  
  
### 更改在 IDE 的颜色  
 您也可以选择更改编辑器中文本、边距指示符、空白和代码元素的默认颜色。  
  
> [!NOTE]
>  若要对操作系统上的所有应用程序窗口使用高对比度的颜色，请按**左 Alt\+左 Shift\+Print Screen**。  如果 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 是打开的，请关闭并重新打开 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 以完全实现高对比度的颜色。  
  
##### 更改编辑器中项的颜色  
  
1.  从**“工具”**菜单中选择**“选项”**。  
  
2.  从**“环境”**文件夹中选择**“字体和颜色”**。  
  
3.  在**“显示其设置”**中选择**“文本编辑器”**。  
  
4.  从**“显示项”**中选择要更改其显示方式的项，如**“纯文本”**、**“指示器边距”**、**“可见空白”**、**“HTML 特性名称”**或**“XML 特性”**。  
  
5.  从下列选项中选择显示设置：**“项前景”**、**“项背景”**和**“粗体”**。  
  
6.  选择**“确定”**。  
  
## 工具栏  
 为了提高工具栏的可用性和易用性，可将文本添加到工具栏按钮。  
  
#### 为工具栏按钮指定文本  
  
1.  在**“工具”**菜单上选择**“自定义”**。  
  
2.  在**“自定义”**对话框中选择**“命令”**选项卡。  
  
3.  选择**“工具栏”**，然后选择含有您要显示其文本的按钮的工具栏名称。  
  
4.  在列表中，选择您要更改的命令。  
  
5.  选择**“修改选中的内容”**。  
  
6.  选择**“图像与文本”**。  
  
#### 修改按钮的显示文本  
  
1.  重新选择**“更改所选内容”**。  
  
2.  在 **名称**附近，插入为所选按钮提供了新的标题。  
  
## 请参阅  
 [Visual Studio 的辅助功能](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [用于设计支持辅助功能的应用程序的资源](../../ide/reference/resources-for-designing-accessible-applications.md)