---
title: "选项，文本编辑器，基本 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Visual_Basic.Editor"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.Editor"
  - "VS.ToolsOptionsPages.Visual_Basic_Editor.Editor"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage"
  - "VS.ToolsOptionsPages.Text_Editor.Basic"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific"
helpviewer_keywords: 
  - "“Basic 文本编辑器选项”对话框"
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 选项，文本编辑器，基本 (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在**“选项”**（**“工具”**菜单中）对话框的**“文本编辑器”**文件夹下的**“Basic”**文件夹中，**“VB 专用”**属性页包含下列属性：  
  
 **自动插入 End 构造**  
 当键入一个过程声明的第一行（如 `Sub Main—`）并按 Enter 时，文本编辑器会添加一个匹配的 `End Sub` 行。  同样地，如果添加一个 [For](/dotnet/visual-basic/language-reference/statements/for-next-statement) 循环，文本编辑器将添加一个匹配的 `Next` 语句。  选定此选项后，代码编辑器自动添加结束构造。  
  
 **整齐排列代码（重新格式化）**  
 文本编辑器适当地重新设置代码的格式。  选中此选项后，代码编辑器将执行以下操作：  
  
-   使代码与正确的制表符位置对齐  
  
-   重新确定关键字、变量和对象的大小写，以符合正确的形式  
  
-   向 `If...Then` 语句中添加缺少的 `Then`。  
  
-   在函数调用中添加括号  
  
-   在字符串中添加缺少的结束引号  
  
-   重新设置指数表示法的格式  
  
-   重新设置日期格式  
  
 **启用大纲模式**  
 在代码编辑器中打开一个文件时，可以在大纲显示模式中查看该文档。  有关更多信息，请参见[大纲显示](../../ide/outlining.md)。  选定了此选项后，打开文件时将激活大纲显示功能。  
  
 **自动插入 Interface 和 MustOverride 成员**  
 当您为类提交 `Implements` 语句或 `Inherits` 语句时，文本编辑器分别为必须实现或必须重写的成员插入原型。  
  
 **显示过程行分隔符**  
 文本编辑器指示过程的可视范围。  在项目的 .vb 源文件中，在下表列出的位置绘制行：  
  
|.vb 源文件中的位置|行位置示例|  
|-----------------|-----------|  
|在块声明构造结束之后|-   在类、结构、模块、接口或枚举的末尾<br />-   在属性、函数或子类之后<br />-   不在属性中的 get 和 set 子句之间|  
|在一组单行构造之后|-   在类文件中的导入语句之后，在类定义之前<br />-   在类中声明的变量之后，在所有过程之前|  
|在单行声明（非块级声明）之后|-   在导入语句、继承语句、变量声明、事件声明、委托声明和 DLL 声明语句之后|  
  
 **启用错误纠正建议**  
 文本编辑器可以建议常见错误的解决方案，并且允许您选择适当的更正，然后将该更正应用于代码。  
  
 **启用引用和关键字的突出显示**  
 文本编辑器可突出显示符号的所有实例或子句中的所有关键字，如 `If..Then`、`While...End While` 或 `Try...Catch...Finally`。  可通过按下 CTRL\+SHIFT\+ 向下箭头或 CTRL\+SHIFT\+向上箭头在突出显示的引用或关键之间浏览。  
  
## 请参阅  
 [“选项”对话框 \-\>“环境”\-\>“常规”](../../ide/reference/general-environment-options-dialog-box.md)   
 [选项，文本编辑器，所有语言，选项卡](../../ide/reference/options-text-editor-all-languages-tabs.md)