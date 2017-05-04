---
title: "XMLNodes 控件 | Microsoft Docs"
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
  - "XMLNodes 控件"
  - "XMLNodes 控件, 事件"
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# XMLNodes 控件
  **重要事项** 有关 Microsoft Word 的本主题开头的信息对于位于美国境外及其领土或使用对单个的优点和使用完全呈现和组织，或者运行的开发的程序，即在 2010 年一月之前的 Microsoft 许可证的 Microsoft Word 产品，那么，当 Microsoft 从 Microsoft Word 移除了特殊功能的实现与自定义 XML 相关。  凡位于美国及其各州内的个体或组织，在使用或开发用于在由 Microsoft 于 2010 年 1 月 10 日之后授予许可的 Microsoft Word 产品上运行的程序时，请勿参考或使用此与 Microsoft Word 相关的信息；这些产品与此许可日期之前的产品，或在美国以外的国家\/地区销售和授予使用许可的产品的行为不同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件是用于公开事件的已映射 XML 节点对象的集合。  只有在将重复架构元素映射到 Microsoft Office Word 文档上时，才会创建 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件。  如果重复元素包含子元素，每个子元素也将作为 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件被创建。  
  
 在 Visual Studio 创建了 XML 节点的集合后，您便可以直接针对该控件编程，而不必遍历 Word 对象模型。  只能通过从文档中移除元素映射来删除 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件。  
  
> [!NOTE]  
>  如果通过 <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> 属性访问 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件的子元素，它将返回 <xref:Microsoft.Office.Interop.Word.XMLNode> 对象，而不是 <xref:Microsoft.Office.Tools.Word.XMLNode> 控件。  有关更多信息，请参见[宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
## 将数据绑定到控件  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件不支持数据绑定。  这是因为 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件不具备复杂数据绑定功能，而简单数据绑定又不能表示重复数据。  
  
## 格式设置  
 可对文档中的文本应用的所有格式设置都可应用于 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件。  
  
## 事件  
 对于 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件可用的事件有：  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## 比较事件  
 您可以捕获用户在特定 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件的上下文中移动其光标时的事件。  例如，您可能有一个名为 `Customer` 的 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件，该控件包含一个名为 `Company` 的 <xref:Microsoft.Office.Tools.Word.XMLNodes> 子控件，而 `Company` 有两个名称分别为 `CompanyName` 和 `CompanyRegion` 的 <xref:Microsoft.Office.Tools.Word.XMLNodes> 子控件，如下所示：  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 如果每次将光标移入 `Company` 节点时都要在操作窗格中显示控件，光标在 `CompanyName` 中还是在 `CompanyRegion` 中并不重要，因为它们同在 `Company` 的上下文中。  在这种情况下，可以在 `Company` 的 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 事件中编写代码。  
  
 在大多数情况下，当光标进入 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件时，会同时引发 <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> 和 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 事件。  下表显示了这些事件之间的差异。  
  
|Select 事件|ContextEnter 事件|  
|---------------|---------------------|  
|当光标放置在 <xref:Microsoft.Office.Tools.Word.XMLNodes> 集合的一个节点中时发生此事件。|当光标从节点上下文以外的区域移入 <xref:Microsoft.Office.Tools.Word.XMLNodes> 集合的节点或子代节点之一时发生。  换言之，只有在上下文发生更改时才会引发此事件，而且多层嵌套的 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件也可能引发此事件。|  
  
 例如，从 `Customer` 之外将光标移到 `CompanyName` 中时，会引发 `Customer`、`Company` 和 `CompanyName` 的 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 事件。  如果再将光标从 `CompanyName` 移动至 `CompanyRegion`，只会引发 `CompanyRegion` 的 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 事件，因为上下文对于 `Company` 和 `Customer` 都相同。  文档中可以包含多个 `Company` 节点。  如果将光标从一个 `Company` 的 `CompanyName` 节点移动至另一个 `Company` 的 `CompanyName` 节点，由于上下文相同，因此只会引发 <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> 事件。  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> 事件和 <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> 事件之间存在着同样的差异。  
  
## 请参阅  
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode 控件](../vsto/xmlnode-control.md)   
 [如何：向 Word 文档添加 XMLNodes 控件](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [如何：将架构映射到 Visual Studio 内部的 Word 文档](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  