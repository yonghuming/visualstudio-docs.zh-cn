---
title: "XMLNode 控件 |Microsoft 文档"
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
helpviewer_keywords: XMLNode control
ms.assetid: 4f5c7f17-62aa-483c-ab0d-b04614ab065d
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c35726314dc679289554e24d4150da4294cf8a0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="xmlnode-control"></a>XMLNode 控件
  **重要**提出有关 Microsoft Word 本主题中的信息不提供的以独占方式适合的好处和使用个人和组织用户位于美国和其区域之外，或使用，或开发在运行的程序，在 2010 年 1 月，Microsoft 中删除的特定功能实现的时间之前已授权的 Microsoft 的 Microsoft Word 产品被与 Microsoft Word 自定义 XML。 有关 Microsoft Word 此信息不能读取或使用的个人或美国或其地区熟悉使用，或开发在 Microsoft Word 2010 年 1 月 10 日之后已授权的 Microsoft 的产品运行的程序中的组织;这些产品将无法与产品许可在该日期之前或购买并获得美国以外的使用许可相同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode>控件是公开事件并能绑定到数据的映射的 XML 节点对象。 <xref:Microsoft.Office.Tools.Word.XMLNode>仅当非重复架构元素映射到 Microsoft Office Word 文档时创建控件。 Visual Studio 创建的 XML 节点后，你可以对其编程直接而无需遍历 Word 对象模型。  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode>可以仅通过在 Word 中删除元素映射中删除控件。  
  
## <a name="binding-data-to-the-control"></a>将数据绑定到控件  
 <xref:Microsoft.Office.Tools.Word.XMLNode>控件支持简单数据绑定。 应通过使用到数据源绑定的 XML 节点<xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>属性。 如果在绑定数据集中的数据进行了更新，<xref:Microsoft.Office.Tools.Word.XMLNode>控件会反映这些变化。  
  
## <a name="formatting"></a>格式设置  
 格式设置也可应用于<xref:Microsoft.Office.Interop.Word.XMLNode>对象可以应用于<xref:Microsoft.Office.Tools.Word.XMLNode>控件。 这包括字体、 下划线样式和字符样式。  
  
## <a name="events"></a>事件  
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
  
## <a name="comparing-events"></a>比较事件  
 你可以捕获事件时用户将他或她的特定上下文中的光标<xref:Microsoft.Office.Tools.Word.XMLNode>控件。 例如，你可能必须<xref:Microsoft.Office.Tools.Word.XMLNode>控件名为`Customer`有一个子<xref:Microsoft.Office.Tools.Word.XMLNode>控件名为`Company`，和`Company`包含两个子<xref:Microsoft.Office.Tools.Word.XMLNode>控件名为`CompanyName`和`CompanyRegion`，如下所示：  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 如果你想要显示操作窗格上的一个控件每当光标移动到`Company`节点，并应重要是否光标置于`CompanyName`或`CompanyRegion`因为它们的上下文中是否`Company`。 在这种情况下，在编写代码<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>事件`Company`。  
  
 在大多数情况下，当光标进入<xref:Microsoft.Office.Tools.Word.XMLNode>控制，同时<xref:Microsoft.Office.Tools.Word.XMLNode.Select>和<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>引发事件。 下表显示这些事件之间的差异。  
  
|选择事件|ContextEnter 事件|  
|------------------|------------------------|  
|将光标放置在时发生<xref:Microsoft.Office.Tools.Word.XMLNode>。|将光标放置在时发生<xref:Microsoft.Office.Tools.Word.XMLNode>或子代节点，从节点的上下文之外的区域之一。 换而言之，引发该事件仅在上下文更改时。|  
  
 例如，当你将光标移从外部`Customer`到`CompanyName`、<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>事件`Customer`， `Company`，和`CompanyName`引发。 如果你然后移动光标从`CompanyName`到`CompanyRegion`，则只<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>事件`CompanyRegion`因为仍在这两者的上下文中引发`Company`和`Customer`。  
  
 之间存在相同的差异<xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>事件和<xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>事件。  
  
## <a name="see-also"></a>另请参阅  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes 控件](../vsto/xmlnodes-control.md)   
 [如何： 向 Word 文档添加 XMLNode 控件](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [如何： 将架构映射到 Visual Studio 内部的 Word 文档](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [主机项和主机控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  