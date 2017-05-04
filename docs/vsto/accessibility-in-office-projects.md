---
title: "Office 项目中的辅助功能 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "辅助功能 [Visual Studio 中的 Office 开发]"
  - "Visual Studio 中的 Office 开发, 辅助功能"
  - "功能区 [Visual Studio 中的 Office 开发], 快捷键"
  - "快捷键 [Visual Studio 中的 Office 开发]"
ms.assetid: 48efcf1f-ca49-47ce-99f0-cc99f051aeae
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Office 项目中的辅助功能
  Microsoft Visual Studio 和 Microsoft Office 包括许多辅助功能，使用这些辅助功能，您可以生成符合标准辅助功能要求的自定义解决方案。  Microsoft 将在网站上发布辅助功能指南。  有关详细信息，请参见 [Accessibility](http://go.microsoft.com/fwlink/?LinkID=37113)（辅助功能）网站。  
  
 在大多数情况下，Visual Studio 中的 Office 项目符合辅助功能标准或公开了相应的属性，通过设置这些属性可以使您的解决方案可用。  但是，对于某些功能的访问受到限制。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 设计时辅助功能  
  
### 在文档级项目中使用快捷键  
 在 Visual Studio 中打开 Microsoft Office Word 文档或 Microsoft Office Excel 工作簿时，一次只有一个应用程序接收快捷键命令。  默认情况下，Visual Studio 接收所有快捷键命令，但是，通过在**“选项”**对话框的**“键盘设置”**页上选择**“动态键盘方案”**，可以在文档具有焦点时让 Word 或 Excel 接收快捷键命令。  有关更多信息，请参见[“选项”对话框 -&#62;“Microsoft Office 键盘设置”-&#62;“Microsoft Office Word 键盘”](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)和[“选项”对话框 -&#62;“Microsoft Office 键盘设置”-&#62;“Microsoft Office Excel 键盘”](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)。  
  
### 显示文档级项目中功能区的快捷键  
 在 Visual Studio 中打开 Word 文档或 Excel 工作簿时，无法按 Alt 键来查看功能区上选项卡和控件的快捷键。  若要在设计器中打开文档或工作簿时查看快捷键，请执行以下步骤。  
  
##### 查看设计器中功能区选项卡和控件的快捷键  
  
1.  在 Visual Studio 中，在**“工具”**菜单上，单击**“选项”**。  
  
2.  展开**“Office 工具”**节点，并根据需要选择**“Microsoft Office Excel 键盘”**或**“Microsoft Office Word 键盘”**。  
  
3.  选择**“动态键盘方案”**。  
  
     将出现一条消息，指明您必须重新启动 Visual Studio 才能使更改生效。  
  
4.  单击**“确定”**。  
  
5.  重新启动 Visual Studio，并重新打开项目。  
  
6.  打开项目的文档或工作簿设计器。  
  
7.  按 F6 显示功能区的快捷键。  
  
## 运行时辅助功能  
  
### Office 文档中的 Windows 窗体控件  
 Windows 窗体控件公开了辅助功能属性以提供与控件的辅助功能（例如屏幕读取器）有关的信息。  当控件位于文档级自定义项中的 Office 文档上时，可以利用这些辅助功能属性。  有关更多信息，请参见[为 Windows 窗体上的控件提供辅助功能信息](http://msdn.microsoft.com/library/887dee6f-5059-4d57-957d-7c6fcd4acb10)。  
  
 但是，如果 Windows 窗体控件承载于 Excel 工作簿或 Word 文档中，则运行时存在一些辅助功能限制：  
  
-   不能使用 Tab 键从一个控件移动到另一个控件。  
  
-   在将文档的缩放设置更改为 100% 之外的其他任何值时，将禁用文档中的控件。  
  
 有关文档中 Windows 窗体控件的限制的信息，请参见 [Office 文档上的 Windows 窗体控件的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)。  
  
### 操作窗格和自定义任务窗格  
 当操作窗格或自定义任务窗格具有焦点时，可以采用访问 Windows 窗体应用程序控件的方式来访问控件。  若要在操作窗格和文档之间移动指针，可以按**“F6”**。  
  
 有关操作窗格和自定义任务窗格的更多信息，请参见[操作窗格概述](../vsto/actions-pane-overview.md)和[自定义任务窗格](../vsto/custom-task-panes.md)。  
  
### 显示模式  
 Visual Studio 具有下列与显示模式相关的限制：  
  
-   在将文档的缩放设置更改为 100% 之外的其他任何值时，将禁用 Word 文档或 Excel 工作表中的控件。  
  
-   如果用户将计算机的辅助功能选项更改为**“使用高对比度”**，则**“新建项目”**对话框将无法正确显示控件。  
  
 您可以使用放大镜来避免这些限制。  放大镜是 Windows 中的一个显示实用工具，它可以创建一个单独的窗口以对屏幕的某一部分进行放大显示。  
  
## 请参阅  
 [开发 Office 解决方案](../vsto/developing-office-solutions.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [为残疾人士提供的辅助功能](../ide/reference/accessibility-for-people-with-disabilities.md)   
 [Visual Studio 的辅助功能](../ide/reference/accessibility-features-of-visual-studio.md)  
  
  