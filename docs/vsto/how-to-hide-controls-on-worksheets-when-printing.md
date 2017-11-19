---
title: "如何： 在打印时隐藏工作表上的控件 |Microsoft 文档"
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
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e89c2f986ffc71892682b9fc8ab60b8810850c2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>如何：在打印时隐藏工作表的控件
  包含 Windows 窗体控件的 Microsoft Office Excel 文档打印时，控件可见。 在打印工作表。 打印工作表时，可以隐藏控件。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  如果你隐藏控件显示数据，如<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>，控件中的数据将不打印工作表上可见。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-hide-controls-when-a-worksheet-is-printed"></a>若要隐藏工作表时的控件打印  
  
1.  创建或打开 Visual Studio 中的 Excel 项目并验证**Sheet1**在设计器中可见。 有关创建项目的信息，请参阅[如何： 创建 Visual Studio 中的 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  从**公共控件**选项卡**工具箱**，拖动<xref:Microsoft.Office.Tools.Excel.Controls.Button>控件拖到单元格上`Sheet1`。  
  
3.  在**属性**窗口中，设置<xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A>属性**False**。  
  
## <a name="see-also"></a>另请参阅  
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [Windows 窗体上的控件 Office 文档概述](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [如何： 添加 Windows 窗体控件添加到 Office 文档](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [如何：调整工作表单元格中的控件大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  