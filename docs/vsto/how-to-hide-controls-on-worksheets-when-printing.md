---
title: "如何：在打印时隐藏工作表的控件 | Microsoft Docs"
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
  - "控件 [Visual Studio 中的 Office 开发], 打印时隐藏"
  - "打印 [Visual Studio 中的 Office 开发], 隐藏控件"
  - "打印 [Visual Studio 中的 Office 开发], 工作表"
  - "工作表, 打印时隐藏控件"
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# 如何：在打印时隐藏工作表的控件
  打印包含 Windows 窗体控件的 Microsoft Office Excel 文档时，控件在打印的工作表上可见。  可以在打印工作表时隐藏这些控件。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  如果隐藏了显示数据的控件，如 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>，则在打印出来的工作表上将看不见该控件中的数据。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 打印工作表时隐藏控件  
  
1.  在 Visual Studio 中创建或打开一个 Excel 项目，并验证**“Sheet1”**在设计器中是否可见。  有关创建项目的信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  从**“工具箱”**的**“公共控件”**选项卡中，将一个 <xref:Microsoft.Office.Tools.Excel.Controls.Button> 控件拖动到 `Sheet1` 上的单元格中。  
  
3.  在**“属性”**窗口中，将 <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> 属性设置为 **False**。  
  
## 请参阅  
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [Office 文档上的 Windows 窗体控件概述](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [如何：为 Office 文档添加 Windows 窗体控件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [如何：调整工作表单元格中的控件的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  