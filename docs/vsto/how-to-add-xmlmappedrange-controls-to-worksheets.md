---
title: "如何：向工作表添加 XMLMappedRange 控件"
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
  - "控件 [Visual Studio 中的 Office 开发], 添加到工作表"
  - "XMLMappedRange 控件, 添加到工作表"
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：向工作表添加 XMLMappedRange 控件
  将 XML 元素映射到 Microsoft Office Excel 中的单元格时，Visual Studio 会自动向工作表中添加一个 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  **“工具箱”**或**“数据源”**窗口中未提供 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件。  另外，不能以编程方式创建 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件。  
  
### 将 XMLMappedRange 控件添加到工作表中  
  
1.  在 Visual Studio 设计器中打开 Excel 工作簿。  
  
2.  打开要添加控件的工作表。  
  
3.  在**“开发工具”**选项卡上单击**“源”**。  
  
    > [!NOTE]  
    >  如果在功能区上看不到**“开发工具”**选项卡，您必须启用该选项卡。  有关更多信息，请参见[如何：在功能区上显示“开发人员”选项卡](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
     随即出现**“XML 源”**任务窗格。  
  
4.  在**“XML 源”**任务窗格中单击**“XML 映射”**。  
  
5.  在**“XML 映射”**对话框中单击**“添加”**。  
  
     随即出现**“XML 源”**对话框。  
  
6.  从**“XML 源”**对话框中选择一个 XML 架构，然后单击**“打开”**。  
  
     该架构被添加到**“XML 映射”**对话框中。  
  
7.  在**“XML 映射”**对话框中单击**“确定”**。  
  
8.  将一个元素从**“XML 源”**任务窗格拖动到工作表上的一个单元格中。  
  
     一个 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 即被创建并添加到项目中。  
  
    > [!NOTE]  
    >  如果从**“XML 源”**任务窗格拖动一个父元素，则会创建一个 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。  
  
## 请参阅  
 [XmlMappedRange 控件](../vsto/xmlmappedrange-control.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [如何：将架构映射到 Visual Studio 内部的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  