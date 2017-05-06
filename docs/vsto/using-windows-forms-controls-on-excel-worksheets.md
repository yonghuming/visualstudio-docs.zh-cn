---
title: "在 Excel 工作表中使用 Windows 窗体控件"
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
  - "控件 [Visual Studio 中的 Office 开发], Windows 窗体控件"
  - "Excel [Visual Studio 中的 Office 开发], Windows 窗体控件"
  - "Windows 窗体控件 [Visual Studio 中的 Office 开发], Excel"
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 在 Excel 工作表中使用 Windows 窗体控件
  可以利用与向 Windows 窗体添加控件相同的方式向 Microsoft Office Excel 工作簿中添加 Windows 窗体控件。  有关在文档上使用控件的一般信息，请参见 [Office 文档上的 Windows 窗体控件概述](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Excel 的控件注意事项  
 有几个特定于 Excel 的注意事项。  
  
### 使控件大小与单元格大小匹配  
 可以将控件设置为当父单元格的大小更改时自动调整大小。  有关更多信息，请参见[如何：调整工作表单元格中的控件的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)。  
  
### 添加由所有工作表共享的组件  
 可以将您希望在所有工作表之间共享的组件（如 <xref:System.Data.DataSet>）添加到工作簿设计器而不是工作表。  该组件将出现在组件栏中。  
  
### 用于嵌入控件的公式  
 在 Excel 中选择一个控件时，**“编辑栏”**中将显示**“\=EMBED\("WinForms.Control.Host",""\)”**。  此文本是必需的，不应删除。  
  
## 请参阅  
 [如何：调整工作表单元格中的控件的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [如何：在打印时隐藏工作表的控件](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [演练：使用 CheckBox 控件更改工作表格式设置](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [演练：使用按钮在工作表的文本框中显示文本](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [演练：使用单选按钮更新工作表中的图表](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  