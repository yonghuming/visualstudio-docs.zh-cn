---
title: "如何： 向工作区中添加架构集搜索结果节点 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 659eaa454243dac8ac05a5f2749237944833da10
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>如何：将架构集搜索结果节点添加到工作区
本主题介绍如何将 XML 架构资源管理器中作为关键字搜索结果突出显示的节点添加到工作区中。  
  
> [!NOTE]
>  只能将全局节点可以添加到[工作区](../xml-tools/xml-schema-designer-workspace.md)。  
  
 此示例使用示例[采购订单架构](../xml-tools/sample-xsd-file-purchase-order-schema.md)。  
  
### <a name="to-add-schema-set-result-nodes"></a>添加架构集结果节点  
  
1.  按照中的步骤[如何： 创建和编辑 XSD 架构文件](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)。  
  
2.  中的搜索文本框中键入"purchaseOrder" [XML 资源管理器](../xml-tools/xml-schema-explorer.md)工具栏，然后单击搜索按钮。  
  
     ![XML 架构资源管理器关键字搜索](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     搜索结果将突出显示在 XML 架构资源管理器中，并用垂直滚动条上的刻度标记。  
  
3.  向工作区添加搜索结果，通过单击**将突出显示的节点添加到工作区**摘要结果窗格上的按钮。  
  
     ![XML 架构资源管理器搜索结果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder`节点和`PurchaseOrderType`节点显示彼此相邻的设计图面上[图形视图](../xml-tools/graph-view.md)。 因为这两个节点相关（`purchaseOrder` 元素属于 `PurchaseOrderType` 类型），因此会在这两个节点之间绘制一个箭头。