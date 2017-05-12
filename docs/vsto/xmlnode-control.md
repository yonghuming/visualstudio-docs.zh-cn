---
title: "XMLNode 控件"
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
  - "XMLNode 控件"
ms.assetid: 4f5c7f17-62aa-483c-ab0d-b04614ab065d
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# XMLNode 控件
  **重要事项** 有关 Microsoft Word 的本主题开头的信息对于位于美国境外及其领土或使用对单个的优点和使用完全呈现和组织，或者运行的开发的程序，即在 2010 年一月之前的 Microsoft 许可证的 Microsoft Word 产品，那么，当 Microsoft 从 Microsoft Word 移除了特殊功能的实现与自定义 XML 相关。  凡位于美国及其各州内的个体或组织，在使用或开发用于在由 Microsoft 于 2010 年 1 月 10 日之后授予许可的 Microsoft Word 产品上运行的程序时，请勿参考或使用此与 Microsoft Word 相关的信息；这些产品与此许可日期之前的产品，或在美国以外的国家\/地区销售和授予使用许可的产品的行为不同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> 控件是一个映射的 XML 节点对象，该对象用于公开事件且可绑定到数据。  仅当非重复架构元素映射到 Microsoft Office Word 文档中时，才创建 <xref:Microsoft.Office.Tools.Word.XMLNode> 控件。  在 Visual Studio 创建了 XML 节点后，您便可以直接对该节点编程，而不必遍历 Word 对象模型。  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> 控件只能通过在 Word 中移除元素映射来删除。  
  
## 将数据绑定到控件  
 <xref:Microsoft.Office.Tools.Word.XMLNode> 控件支持简单数据绑定。  应该使用 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> 属性将 XML 节点绑定到数据源。  如果更新绑定数据集内的数据，则 <xref:Microsoft.Office.Tools.Word.XMLNode> 控件会反映所做的更改。  
  
## 格式设置  
 可应用于 <xref:Microsoft.Office.Interop.Word.XMLNode> 对象的格式设置也可应用于 <xref:Microsoft.Office.Tools.Word.XMLNode> 控件。  其中包括字体、下划线样式和字符样式。  
  
## 事件  
 以下事件可用于 <xref:Microsoft.Office.Tools.Word.XMLNode> 控件：  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## 比较事件  
 您可以捕获用户在特定 <xref:Microsoft.Office.Tools.Word.XMLNode> 控件的上下文中移动其光标时的事件。  例如，您可能有一个名为 `Customer` 的 <xref:Microsoft.Office.Tools.Word.XMLNode> 控件，该控件包含一个名为 `Company` 的 <xref:Microsoft.Office.Tools.Word.XMLNode> 子控件，而 `Company` 有两个名称分别为 `CompanyName` 和 `CompanyRegion` 的 <xref:Microsoft.Office.Tools.Word.XMLNode> 子控件，如下所示：  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 如果每次将光标移入 `Company` 节点时都要在操作窗格中显示控件，光标在 `CompanyName` 中还是在 `CompanyRegion` 中并不重要，因为它们同在 `Company` 的上下文中。  在这种情况下，可以在 `Company` 的 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 事件中编写代码。  
  
 在大多数情况下，当光标进入 <xref:Microsoft.Office.Tools.Word.XMLNode> 控件时，会同时引发 <xref:Microsoft.Office.Tools.Word.XMLNode.Select> 和 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 事件。  下表显示了这些事件之间的差异。  
  
|Select 事件|ContextEnter 事件|  
|---------------|---------------------|  
|当光标放置在 <xref:Microsoft.Office.Tools.Word.XMLNode> 内时发生此事件。|当光标从 <xref:Microsoft.Office.Tools.Word.XMLNode> 节点的上下文外的区域移入该节点或它的一个子节点内时发生此事件。  换而言之，只有在上下文发生更改时才会引发此事件。|  
  
 例如，从 `Customer` 之外将光标移到 `CompanyName` 中时，会引发 `Customer`、`Company` 和 `CompanyName` 的 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 事件。  如果再将光标从 `CompanyName` 移动至 `CompanyRegion`，只会引发 `CompanyRegion` 的 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 事件，因为您仍在 `Company` 和 `Customer` 的上下文中。  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> 事件和 <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> 事件之间存在着同样的差别。  
  
## 请参阅  
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes 控件](../vsto/xmlnodes-control.md)   
 [如何：向 Word 文档添加 XMLNode 控件](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [如何：将架构映射到 Visual Studio 内部的 Word 文档](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  