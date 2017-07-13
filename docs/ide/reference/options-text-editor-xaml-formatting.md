---
title: "“选项”->“文本编辑器”->“XAML”->“格式设置”| Microsoft Docs"
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
caps.latest.revision: 15
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 0d087d735f3db1f1d8fa7f37f049b6208e5242c0
ms.contentlocale: zh-cn
ms.lasthandoff: 05/30/2017

---
# 选项，文本编辑器，XAML，格式
<a id="options-text-editor-xaml-formatting" class="xliff"></a>
使用“格式设置”属性页可指定如何在 XAML 文档中设置元素和特性的格式。 若要打开“选项”对话框，请单击“工具”菜单，然后单击“选项”。 若要访问“格式设置”属性页，请依次展开“文本编辑器”、“XAML”、“格式设置”节点。  

> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)。  

## 自动格式化事件
<a id="auto-formatting-events" class="xliff"></a>  
 检测到以下任一事件时，可能引发自动格式设置。  

-   完成结束标记或简单标记。  

-   完成开始标记。  

-   从剪贴板粘贴。  

-   设置键盘命令格式。  

 可以指定引发自动格式设置的事件。  

|||  
|-|-|  
|**结束标记或简单标记完成时**|完成键入结束标记或简单标记时引发自动格式设置。 简单标记没有特性，例如 `<Button />`。|  
|**开始标记完成时**|完成键入开始标记时引发自动格式设置。|  
|**从剪贴板粘贴时**|将 XAML 从剪贴板粘贴到 XAML 视图时引发自动格式设置。|  

## 引号样式
<a id="quotation-mark-style" class="xliff"></a>  
 此设置指示特性值是括在单引号内，还是括在双引号内。 自动格式设置程序和 IntelliSense 自动完成功能都使用此设置。  

 设置此选项后，受影响的只有随后在 XAML 视图中使用设计器添加或手动添加的特性。  

|||  
|-|-|  
|**双引号 (")**|特性值括在双引号内。<br /><br /> `<Button Name="button1">Hello</Button>`|  
|**单引号 (')**|特性值括在单引号内。<br /><br /> `<Button Name='button1'>Hello</Button>`|  

## 标记换行
<a id="tag-wrapping" class="xliff"></a>  
 可以为标记换行指定一个行长度。 启用标记换行后，随后使用设计器添加的所有 XAML 将进行适当换行。  

|||  
|-|-|  
|**对超出指定长度的标记执行换行**|指定是否在“长度”指定的行长度处换行。|  
|**长度**|一行中可以包含的字符数。 如有必要，某些 XAML 行可以超过指定的行长度。|  

## 特性间距
<a id="attribute-spacing" class="xliff"></a>  
 使用此设置可以控制特性在 XAML 文档中的排列方式  

|||  
|-|-|  
|**在特性之间保留换行符和空格**|特性之间的换行符和空格不受自动格式设置的影响。<br /><br /> `<Button Height="23"   Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**在特性之间插入单个空格**|特性占用一行，由一个空格分隔相邻的特性。 应用标记换行设置。<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|  
|**将各个特性分行放置**|每个特性单占一行。 当存在很多特性时，此设置非常有用。<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**将第一个特性放在与开始标记相同的行上**|选中该项时，第一个特性与元素的开始标记显示在同一行上。<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  

## 元素间距
<a id="element-spacing" class="xliff"></a>  
 使用此设置可以控制元素在 XAML 文档中的排列方式  

|||  
|-|-|  
|**保留内容中的新行**|不移除元素内容中的空行。<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**将内容中的多个空行折叠为单个行**|元素内容中的多个空行会折叠为单个行。<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**移除内容中的空行**|移除元素内容中的所有空行。<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`|  

## “杂项”部分->“自动插入”
<a id="miscellaneous-section-auto-insert" class="xliff"></a>  
 使用此设置可以控制自动生成标记和引号的时间。  

|||  
|-|-|  
|**结束标记**|指定使用大于号字符 (>) 关闭开始标记时，是否自动生成元素的结束标记。|  
|**特性引号**|指定从语句完成下拉列表中选择特性值时，是否生成封闭引号。|  
|**MarkupExtensions 的右大括号**|指定键入左括号字符 ({) 时，是否自动生成标记扩展的右括号 (})。|  
|**用于分隔 MarkupExtension 参数的逗号**|指定在标记扩展中键入多个参数时是否生成逗号。|  

## 另请参阅
<a id="see-also" class="xliff"></a>  
 [WPF 中的 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)   
 [如何：更改 XAML 视图设置](http://msdn.microsoft.com/en-us/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [XAML 和代码演练](http://msdn.microsoft.com/en-us/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)

