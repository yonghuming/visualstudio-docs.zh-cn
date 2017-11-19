---
title: "如何： 在工作表中的数据库记录滚动 |Microsoft 文档"
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
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
ms.assetid: aea4c86c-9d6d-47dd-8977-066e21945dab
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 78ccd24a262863a4d6f844d624ef9996d09d568f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>如何：在工作表中滚动查看数据库记录
  以下过程演示如何使用设计器显示单个字段从数据库表中的 Microsoft Office Excel 工作表，使最终用户能够滚动所有记录的控件。  
  
 仅在文档级项目中，可以使用设计器。 但是，你可以添加控件和将其绑定到数据以编程方式在运行时。 有关详细信息，请参阅[演练： 简单的数据绑定，在 VSTO 外接程序项目](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### <a name="to-scroll-through-database-records-in-a-worksheet"></a>若要滚动工作表中的数据库记录  
  
1.  在 Visual Studio 中打开一个 Excel 应用程序项目。  
  
2.  打开**数据源**窗口并从数据库创建数据源。 有关详细信息，请参阅[添加新连接](../data-tools/add-new-connections.md)。  
  
3.  展开包含你想要显示的数据的表并选择特定列。  
  
4.  打开的控件，然后选择列表**NamedRange**。  
  
5.  拖动<xref:Microsoft.Office.Tools.Excel.NamedRange>拖到想要显示的数据单元格中的控件。  
  
6.  从**Windows 窗体**选项卡**工具箱**，添加<xref:System.Windows.Forms.BindingNavigator>控制转移到你的工作表，并设置你想要使用的控件。 有关详细信息，请参阅[BindingNavigator 控件概述 &#40;Windows 窗体 &#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>另请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  