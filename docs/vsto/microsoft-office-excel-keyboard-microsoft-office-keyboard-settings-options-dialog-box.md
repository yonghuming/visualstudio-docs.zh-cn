---
title: "“选项”对话框 -&gt;“Microsoft Office 键盘设置”-&gt;“Microsoft Office Excel 键盘” | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ExcelOptions.KeyboardMappingScheme"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "键盘快捷方式，Visual Studio 中的 Office 开发"
ms.assetid: 2a8b9e70-66fa-4461-8039-b6d8a2fbb963
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# “选项”对话框 -&gt;“Microsoft Office 键盘设置”-&gt;“Microsoft Office Excel 键盘”
  Microsoft Office Excel 2003 和 Visual Studio 都可处理快捷键。  在 Excel 和 Visual Studio 中，同一个快捷键组合可以代表不同的命令。  在 Visual Studio 的文档级项目中打开 Excel 时，每次仅有一个应用程序接收快捷键命令。  默认情况下，Visual Studio 接收所有的快捷键命令，但通过选择**“动态键盘方案”**，可以在文档具有焦点时让 Excel 快捷键命令。  
  
 如果使用的快捷键在当前处理快捷键的应用程序中没有分配命令，则该快捷键将被传递给另一个应用程序。  
  
 对于 Excel 项目来说，您选择的选项一直有效，直到您更改该选项为止。  所做的选择不会影响 Microsoft Office Word 2003 项目；对于 Word 来说，要进行任何更改都必须使用“Microsoft Office Word 键盘”选项。  
  
## UIElement 列表  
 **Visual Studio 键盘方案**  
 即使 Excel 具有焦点，Visual Studio 也会接收所有的快捷键命令。  例如，当 Excel 含有焦点时，如果按功能键 F5，Visual Studio 将开始调试您的解决方案。  
  
 **动态键盘方案**  
 Visual Studio 只在具有焦点时接收快捷键命令。  当 Excel 具有焦点时，它会接收所有的快捷键命令。  例如，当 Excel 含有焦点时，如果按功能键 F5，Excel 将打开**“转到”**对话框。  如果在 Visual Studio 具有焦点时按功能键 F5，Visual Studio 开始调试您的解决方案。  
  
## 请参阅  
 [“选项”对话框 -&#62;“Microsoft Office 键盘设置”-&#62;“Microsoft Office Word 键盘”](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  