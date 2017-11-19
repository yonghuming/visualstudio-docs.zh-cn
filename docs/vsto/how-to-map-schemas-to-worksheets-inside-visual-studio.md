---
title: "如何： 将架构映射到 Visual Studio 内部的工作表 |Microsoft 文档"
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
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c09c99bc5d8bc964ae3afd82fe7a4a9fd5764edd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>如何：将架构映射到 Visual Studio 内部的工作表
  在 Visual Studio 中打开工作表时，你可以将 XML 架构映射到工作表。 使用相同的 Microsoft Office Excel 工具，你使用 Visual Studio 外部打开工作簿时。 Office 项目创建相同的对象是否将架构映射到工作表之前或之后创建 Excel 解决方案。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  不能在 Excel 解决方案中使用多部分的 XML 架构。  
  
### <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>若要将 XML 架构映射到 Visual Studio 中的 Excel 工作表  
  
1.  打开 Visual Studio 内部的 Excel 工作簿或模板项目。  
  
2.  单击要将焦点移到设计器中的工作表中。  
  
3.  在功能区上，单击 **“开发人员”** 选项卡。  
  
    > [!NOTE]  
    >  如果看不到 **“开发人员”** 选项卡，则必须首先显示它。 有关详细信息，请参阅 [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
4.  在**XML**组中，单击**源**。  
  
     **XML 源**窗口随即打开。  
  
5.  在**XML 源**窗口中，单击**XML 映射**。  
  
     **XML 映射**对话框随即打开。  
  
6.  在**XML 映射**对话框中，单击**添加**。  
  
7.  浏览到你的架构文件，选择它，，然后单击**打开**。  
  
8.  单击“确定”。  
  
     架构便会出现在**XML 源**窗口。 在你的项目中，类型化<xref:System.Data.DataSet>根据架构，生成和<xref:System.Windows.Forms.BindingSource>创建。  
  
9. 将元素从**XML 源**到你的工作表中的位置，想要创建的相应控件的窗口。  
  
     如果您拖动的非重复架构元素，Office 项目生成<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>自动绑定到控件<xref:System.Windows.Forms.BindingSource>。  
  
     如果将重复架构元素拖动时，Office 项目生成<xref:Microsoft.Office.Tools.Excel.ListObject>不会自动绑定到数据源的控件。 有关详细信息，请参阅[XML 架构和文档级自定义项中的数据](../vsto/xml-schemas-and-data-in-document-level-customizations.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 将架构映射到 Visual Studio 内部的 Word 文档](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [文档级自定义项中的 XML 架构和数据](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  