---
title: "XMLNodes 控件 |Microsoft 文档"
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
- XMLNodes control, events
- XMLNodes control
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2950d1c9bf2edb0715ad588180cec3b5e17da265
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="xmlnodes-control"></a>XMLNodes 控件
  **重要**提出有关 Microsoft Word 本主题中的信息不提供的以独占方式适合的好处和使用个人和组织用户位于美国和其区域之外，或使用，或开发在运行的程序，在 2010 年 1 月，Microsoft 中删除的特定功能实现的时间之前已授权的 Microsoft 的 Microsoft Word 产品被与 Microsoft Word 自定义 XML。 有关 Microsoft Word 此信息不能读取或使用的个人或美国或其地区熟悉使用，或开发在 Microsoft Word 2010 年 1 月 10 日之后已授权的 Microsoft 的产品运行的程序中的组织;这些产品将无法与产品许可在该日期之前或购买并获得美国以外的使用许可相同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes>控件是公开事件映射的 XML 节点对象的集合。 <xref:Microsoft.Office.Tools.Word.XMLNodes>仅当将重复架构元素映射到 Microsoft Office Word 文档时创建控件。 如果重复元素包含子元素，每个子元素也作为创建<xref:Microsoft.Office.Tools.Word.XMLNodes>控件。  
  
 Visual Studio 创建的 XML 节点集合后，可以直接而无需遍历 Word 对象模型编程控件。 <xref:Microsoft.Office.Tools.Word.XMLNodes>可以仅通过从文档中移除的元素映射中删除控件。  
  
> [!NOTE]  
>  如果访问的子元素<xref:Microsoft.Office.Tools.Word.XMLNodes>通过控制<xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A>属性，它返回<xref:Microsoft.Office.Interop.Word.XMLNode>对象而不是<xref:Microsoft.Office.Tools.Word.XMLNode>控件。 有关更多信息，请参见 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
## <a name="binding-data-to-the-control"></a>将数据绑定到控件  
 <xref:Microsoft.Office.Tools.Word.XMLNodes>控件不支持数据绑定。 这是因为<xref:Microsoft.Office.Tools.Word.XMLNodes>控件不具有复杂数据绑定功能，，简单数据绑定不能表示重复数据。  
  
## <a name="formatting"></a>格式设置  
 可以向文档中的文本应用任何格式设置可应用于<xref:Microsoft.Office.Tools.Word.XMLNodes>控件。  
  
## <a name="events"></a>事件  
 可用于事件<xref:Microsoft.Office.Tools.Word.XMLNodes>控件：  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="comparing-events"></a>比较事件  
 你可以捕获事件时用户将他或她的特定上下文中的光标<xref:Microsoft.Office.Tools.Word.XMLNodes>控件。 例如，你可能必须<xref:Microsoft.Office.Tools.Word.XMLNodes>控件名为`Customer`有一个子<xref:Microsoft.Office.Tools.Word.XMLNodes>控件名为`Company`，和`Company`包含两个子<xref:Microsoft.Office.Tools.Word.XMLNodes>控件名为`CompanyName`和`CompanyRegion`，如下所示：  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 如果你想要显示操作窗格上的一个控件每当光标移动到`Company`节点，并应重要是否光标置于`CompanyName`或`CompanyRegion`因为它们的上下文中是否`Company`。 在这种情况下，在编写代码<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>事件`Company`。  
  
 在大多数情况下，当光标进入<xref:Microsoft.Office.Tools.Word.XMLNodes>控制，同时<xref:Microsoft.Office.Tools.Word.XMLNodes.Select>和<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>引发事件。 下表显示这些事件之间的差异。  
  
|选择事件|ContextEnter 事件|  
|------------------|------------------------|  
|将光标放置在的节点之一时发生<xref:Microsoft.Office.Tools.Word.XMLNodes>集合。|将光标放置在节点或子代节点之一时发生<xref:Microsoft.Office.Tools.Word.XMLNodes>集合，从节点的上下文之外的区域。 换而言之，它仅更改时引发的上下文，并会引发多层嵌套<xref:Microsoft.Office.Tools.Word.XMLNodes>控件。|  
  
 例如，当你将光标移从外部`Customer`到`CompanyName`、<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>事件`Customer`， `Company`，和`CompanyName`引发。 如果你然后移动光标从`CompanyName`到`CompanyRegion`、<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>事件仅为`CompanyRegion`引发，因为上下文为相同`Company`和`Customer`。 你可以有多个`Company`在文档中的节点。 如果你移动光标从`CompanyName`之一的节点`Company`到`CompanyName`另一个节点`Company`，上下文是相同的因此仅<xref:Microsoft.Office.Tools.Word.XMLNodes.Select>引发事件。  
  
 之间存在相同的差异<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>事件和<xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>事件。  
  
## <a name="see-also"></a>另请参阅  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode 控件](../vsto/xmlnode-control.md)   
 [如何： 向 Word 文档添加 XMLNodes 控件](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [如何： 将架构映射到 Visual Studio 内部的 Word 文档](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [主机项和主机控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  