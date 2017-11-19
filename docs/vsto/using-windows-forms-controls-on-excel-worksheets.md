---
title: "使用 Windows 窗体的 Excel 工作表上的控件 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bbd9c19698a9c81b5af29d27bba91b8aa36dcd2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-windows-forms-controls-on-excel-worksheets"></a>在 Excel 工作表中使用 Windows 窗体控件
  相同的方式将控件添加到 Windows 窗体中，可以将 Windows 窗体控件添加到您的 Microsoft Office Excel 工作簿。 有关使用文档上的控件的常规信息，请参阅[Office 文档概述上的 Windows 窗体控件](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>有关 Excel 控件注意事项  
 有几个特定于 Excel 的注意事项。  
  
### <a name="matching-control-size-to-cell-size"></a>单元格大小匹配控件大小  
 可以将控件设置为当父单元格的大小更改时自动重设大小。 有关详细信息，请参阅[如何： 在工作表单元格调整控件](../vsto/how-to-resize-controls-within-worksheet-cells.md)。  
  
### <a name="adding-components-that-are-shared-by-all-worksheets"></a>添加由所有工作表共享的组件  
 可以将希望在所有工作表之间共享的组件（如 <xref:System.Data.DataSet>）添加到工作簿设计器而不是工作表。 该组件将出现在组件栏中。  
  
### <a name="formula-for-embedding-controls"></a>嵌入控件的公式  
 当在 Excel 中选择一个控件时， **“公式栏”** 中将显示 **=EMBED("WinForms.Control.Host","")**。 此文本是必需的并且不应删除。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 调整工作表单元格中的控件的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [如何： 在打印时隐藏工作表上的控件](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [演练： 更改工作表格式设置使用复选框控件](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [演练： 使用按钮在工作表的文本框中显示文本](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [演练：使用单选按钮更新工作表中的图表](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  