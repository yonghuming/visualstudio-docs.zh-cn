---
title: "Microsoft Office Word 键盘，Microsoft Office 键盘设置选项对话框中 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords: keyboard shortcuts, Office development in Visual Studio
ms.assetid: d98edaab-846a-4baa-b190-702b1134754c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bbce725246356086ac64b1810b80b91839caea3c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>“选项”对话框 ->“Microsoft Office 键盘设置”->“Microsoft Office Word 键盘”
  Microsoft Office Word 和 Visual Studio 同时处理键盘快捷方式。 相同的快捷组合键可以代表不同的命令，在 Word 和 Visual Studio 中的内容。 在 Visual Studio 中的文档级项目中打开 Word 时，一次只有一个应用程序接收的快捷键命令。 默认情况下，Visual Studio 接收所有快捷键命令，但你可以在该文档通过选择具有焦点时接收它们的 Word**动态键盘方案**。  
  
 如果你使用未分配给当前正在处理键盘快捷方式应用程序中的命令的快捷键，则该快捷键将被传递到其他应用程序。  
  
 你选择的选项将对于 Word 项目实际上保留，直至你更改它。 所选内容不会影响 Microsoft Office Excel 项目;你必须进行任何更改 Excel 使用 Microsoft Office Excel 键盘选项。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **Visual Studio 键盘方案**  
 Visual Studio 接收所有快捷键命令，即使 Word 文档具有焦点。 例如，如果该文档具有焦点时按 F5 功能键，Visual Studio 启动调试你的解决方案。  
  
 **动态键盘方案**  
 仅当它具有焦点时，visual Studio 将接收的快捷键命令。 当 Word 文档具有焦点时，Word 将接收所有的快捷键命令。 例如，如果当 Word 文档具有焦点时按 F5 功能键，Word 会打开**查找和替换** 癸杠**转到**选定选项卡。 如果您在 Visual Studio 具有焦点时按 F5，Visual Studio 将启动调试你的解决方案。  
  
## <a name="see-also"></a>另请参阅  
 [“选项”对话框 ->“Microsoft Office 键盘设置”->“Microsoft Office Excel 键盘”](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  