---
title: "如何：向工作表添加 Chart 控件"
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
  - "图表控件 [Visual Studio 中的 Office 开发], 添加到工作表"
  - "控件 [Visual Studio 中的 Office 开发], 添加到工作表"
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 如何：向工作表添加 Chart 控件
  你可以在设计时和运行时将 <xref:Microsoft.Office.Tools.Excel.Chart> 控件添加到在文档级自定义项中的 Microsoft Office Excel 工作表。  还可以在运行时将 <xref:Microsoft.Office.Tools.Excel.Chart> 控件添加到 VSTO 外接程序中。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 本主题介绍了以下任务：  
  
-   [在设计时添加图表控件](#designtime)  
  
-   [在运行时将图表控件添加到文档级项目中](#runtimedoclevel)  
  
-   [在运行时将图表控件添加到 VSTO 外接程序项目中](#runtimeaddin)  
  
 有关 <xref:Microsoft.Office.Tools.Excel.Chart> 控件的详细信息，请参阅[Chart 控件](../vsto/chart-control.md)。  
  
##  <a name="designtime"></a> 在设计时添加图表控件  
 可按照与从应用程序添加图表相同的方式，将 <xref:Microsoft.Office.Tools.Excel.Chart> 控件添加到工作表中。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart> 控件在**“工具箱”**或**“数据源”**窗口中不可用。  
  
#### 将图表主机控件添加到 Excel 的工作表中  
  
1.  在**“插入”**选项卡上的**“图表”**组中，依次单击**“列”**、一个图表类别和所需的图表类型。  
  
2.  在**“插入图表”**对话框中，单击**“确定”**。  
  
3.  在**“设计”**选项卡上的**“数据”**组中，单击**“选择数据”**。  
  
4.  在**“选择数据源”**对话框中，单击**“图表数据范围”**框，并清除所有默认选择。  
  
5.  在**“图表数据”**表中，选择包含图表数据的单元格范围（单元格 **A5** 到 **D8**）。  
  
6.  在**“选择数据源”**对话框中，单击**“确定”**。  
  
##  <a name="runtimedoclevel"></a> 在运行时将图表控件添加到文档级项目中  
 可以在运行时动态添加 <xref:Microsoft.Office.Tools.Excel.Chart> 控件。  文档关闭时，动态创建的图表不会作为主机控件保留在文档中。  有关详细信息，请参阅[在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### 以编程方式将图表控件添加到工作表中  
  
1.  在 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件处理程序中，插入下列代码以添加 <xref:Microsoft.Office.Tools.Excel.Chart> 控件。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> 在运行时将图表控件添加到 VSTO 外接程序项目中  
 可以按编程方式将 <xref:Microsoft.Office.Tools.Excel.Chart> 控件添加到 VSTO 外接程序项目中任何打开的工作表中。  有关详细信息，请参阅[在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
 工作表关闭时，动态创建的图表控件不会作为主机控件保留在工作表中。  有关详细信息，请参阅[在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### 以编程方式将图表控件添加到工作表中  
  
1.  下面的代码将生成基于打开工作表的工作表主机项，然后添加 <xref:Microsoft.Office.Tools.Excel.Chart> 控件。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#9)]  
  
## 编译代码  
 此示例具有下列要求：  
  
-   制成图表并存储在工作表中 A5 到 D8 范围内的数据。  
  
## 请参阅  
 [在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [Chart 控件](../vsto/chart-control.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  