---
title: "如何：将架构映射到 Visual Studio 内部的工作表 | Microsoft Docs"
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
  - "Excel [Visual Studio 中的 Office 开发], XML 架构"
  - "映射 [Visual Studio 中的 Office 开发], XML 架构到 Excel 工作表"
  - "工作表 [Visual Studio 中的 Office 开发], XML 架构"
  - "XML 架构 [Visual Studio 中的 Office 开发], 映射"
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 如何：将架构映射到 Visual Studio 内部的工作表
  当工作表在 Visual Studio 项目中打开时，可以将 XML 架构映射到该工作表。  所使用的工具与在 Visual Studio 外部打开工作簿时所用的 Microsoft Office Excel 工具相同。  不管是在创建 Excel 解决方案之前还是之后将架构映射到工作表，Office 项目都会创建相同的对象。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  不能在 Excel 解决方案中使用多部分 XML 架构。  
  
### 将 XML 架构映射到 Visual Studio 中的 Excel 工作表  
  
1.  在 Visual Studio 内打开 Excel 工作簿或模板项目。  
  
2.  在工作表中单击，以将焦点移至设计器中。  
  
3.  在功能区上，单击**“开发人员”**选项卡。  
  
    > [!NOTE]  
    >  如果看不到**“开发人员”**选项卡，您必须首先显示该选项卡。  有关更多信息，请参见[如何：在功能区上显示“开发人员”选项卡](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
4.  在**“XML”**组中，单击**“源”**。  
  
     随即打开**“XML 源”**窗口。  
  
5.  在**“XML 源”**窗口中单击**“XML 映射”**。  
  
     随即打开**“XML 映射”**对话框。  
  
6.  在**“XML 映射”**对话框中单击**“添加”**。  
  
7.  浏览至架构文件，选择该文件，然后单击**“打开”**。  
  
8.  单击**“确定”**。  
  
     架构便会出现在**“XML 源”**窗口中。  在您的项目中，会根据架构生成一个类型化 <xref:System.Data.DataSet>，并创建一个 <xref:System.Windows.Forms.BindingSource>。  
  
9. 将元素从**“XML 源”**窗口拖放到工作表中要创建相应控件的位置。  
  
     如果拖动非重复架构元素，Office 项目生成自动绑定到 <xref:System.Windows.Forms.BindingSource>的一个 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件。  
  
     如果拖动重复架构元素，Office 项目生成不会自动绑定到数据源的一个 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。  有关更多信息，请参见[文档级自定义项中的 XML 架构和数据](../vsto/xml-schemas-and-data-in-document-level-customizations.md)。  
  
## 请参阅  
 [如何：将架构映射到 Visual Studio 内部的 Word 文档](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [文档级自定义项中的 XML 架构和数据](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  