---
title: "如何：向工作表添加 ListObject 控件 | Microsoft Docs"
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
  - "ListObject 控件，添加到工作表"
  - "控件 [Visual Studio 中的 Office 开发]，添加到工作表"
ms.assetid: 40788ecb-937f-4d2a-90ba-9c938e495b74
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：向工作表添加 ListObject 控件
  在文档级项目中，你可以在设计时和运行时将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件添加到 Microsoft Office Excel 工作表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 你也可以在 VSTO 外接程序项目中，在运行时添加 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。  
  
 本主题介绍了以下任务：  
  
-   [在设计时添加 ListObject 控件](#designtime)  
  
-   [在运行时在文档级项目中添加 ListObject 控件](#runtimedoclevel)  
  
-   [在运行时在 VSTO 外接程序项目中添加 ListObject 控件](#runtimeaddin)  
  
 有关 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件的详细信息，请参阅 [ListObject 控件](../vsto/listobject-control.md)。  
  
##  <a name="designtime"></a> 在设计时添加 ListObject 控件  
 有多种方法可在设计时在文档级项目中将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件添加到工作表：从 Excel、从 Visual Studio“工具箱”，以及从“数据源”窗口。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### 在 Excel 中使用功能区  
  
1.  在“插入”选项卡上，单击“表”组中的“表”。  
  
2.  选择要包含在列表中的一个或多个单元格，然后单击“确定”。  
  
#### 使用工具箱  
  
1.  从“工具箱”的“Excel 控件”选项卡上，拖动 <xref:Microsoft.Office.Tools.Excel.ListObject> 到工作表。  
  
     “添加 ListObject 控件”对话框随即出现。  
  
2.  选择要包含在列表中的一个或多个单元格，然后单击“确定”。  
  
     如果不希望保留默认名称，可以在“属性”窗口中更改名称。  
  
#### 使用“数据源”窗口  
  
1.  打开“数据源”窗口并为项目创建数据源。 有关详细信息，请参阅[如何：连接到数据库中的数据](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)。  
  
2.  将表从“数据源”窗口拖到工作表中。  
  
     数据绑定 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件将添加到工作表中。 有关详细信息，请参阅[数据绑定和 Windows 窗体](../Topic/Data%20Binding%20and%20Windows%20Forms.md)。  
  
##  <a name="runtimedoclevel"></a> 在运行时在文档级项目中添加 ListObject 控件  
 可以在运行时动态添加 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。 这使得你可以创建宿主控件以响应事件。 工作表关闭时，动态创建的列表对象不作为宿主控件保留在工作表中。 有关更多信息，请参见[在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### 以编程方式将 ListObject 控件添加到工作表中  
  
1.  在 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件处理程序中，插入下列代码以将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件添加到 **A1** 至 **A4** 单元格。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> 在运行时在 VSTO 外接程序项目中添加 ListObject 控件  
 可以按编程方式将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件添加到 VSTO 外接程序项目中任何打开的工作表中。 工作表保存并关闭时，动态创建的列表对象不作为宿主控件保留在工作表中。 有关详细信息，请参阅[在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
#### 以编程方式将 ListObject 控件添加到工作表中  
  
1.  下面的代码将生成基于打开工作表的工作表宿主项，然后将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件添加到 **A1** 至 **A4** 单元格。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#8)]  
  
## 请参阅  
 [在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [ListObject 控件](../vsto/listobject-control.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [如何：调整 ListObject 控件的大小](../vsto/how-to-resize-listobject-controls.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  