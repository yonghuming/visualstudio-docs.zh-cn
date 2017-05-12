---
title: "“选项”对话框 -&gt;“Microsoft Office 键盘设置”-&gt;“Microsoft Office Word 键盘” | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard"
  - "VST.WordOptions.KeyboardMappingScheme"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "键盘快捷方式，Visual Studio 中的 Office 开发"
ms.assetid: d98edaab-846a-4baa-b190-702b1134754c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# “选项”对话框 -&gt;“Microsoft Office 键盘设置”-&gt;“Microsoft Office Word 键盘”
  Microsoft Office Word 和 Visual Studio 都可处理快捷键。  在 Word 和 Visual Studio 中同样的快捷键组合可代表不同的命令。  在 Visual Studio 的文档级项目中打开 Word 时，每次仅有一个应用程序接收快捷键命令。  默认情况下，Visual Studio 接收所有的快捷键命令，但通过选择**“动态键盘方案”**，在文档具有焦点时可以使 Word 接收快捷键命令。  
  
 如果使用的快捷键在当前处理快捷键的应用程序中没有分配命令，则该快捷键将被传递给另一个应用程序。  
  
 此更改选项之前，它对 Word 项目保持有效。  选择该选项不影响 Microsoft Office Excel 项目；必须使用“Microsoft Office Excel 键盘”选项对 Excel 进行更改。  
  
## UIElement 列表  
 **Visual Studio 键盘方案**  
 Visual Studio 接收所有的快捷键命令，即使 Word 文档具有焦点亦如此。  例如，如果在文档具有焦点时按功能键 F5，Visual Studio 会开始调试您的解决方案。  
  
 **动态键盘方案**  
 Visual Studio 只在具有焦点时接收快捷键命令。  当 Word 文档具有焦点时，它接收所有的快捷键命令。  例如，如果当 Word 文档具有焦点时按功能键 F5，则 Word 会打开**“查找和替换”**对话框并选中**“定位”**选项卡。  如果在 Visual Studio 具有焦点时按功能键 F5，Visual Studio 开始调试您的解决方案。  
  
## 请参阅  
 [“选项”对话框 -&#62;“Microsoft Office 键盘设置”-&#62;“Microsoft Office Excel 键盘”](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  