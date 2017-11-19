---
title: "如何： 检查节点上使用内容模型视图的内容模型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32b87cf771b0eda1ba58973dbc2c197f4898dfd8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>如何：使用内容模型视图检查节点的内容模型
本主题描述如何浏览节点使用[内容模型视图](../xml-tools/content-model-view.md)。  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>创建新的 XSD 文件并显示内容模型视图中的根元素  
  
1.  创建新的 XML 架构文件。  
  
2.  单击**使用 XML 编辑器查看和编辑基础 XML 架构文件**起始视图上。  
  
3.  复制 XML 架构示例代码从[示例 XML 架构： 订单架构](../xml-tools/sample-xsd-file-purchase-order-schema.md)并将其以替换默认情况下，已将它们添加到新 XSD 文件的代码粘贴。  
  
4.  选择`purchaseOrder`通过右键单击架构资源管理器中的元素`purchaseOrder`元素在 XML 编辑器中，然后选择**XML 资源管理器中显示**。  
  
5.  右键单击`purchaseOrder`中的 XML 资源管理器和选择**在内容模型视图中显示**。  
  
     内容模型视图显示设计图面上的 `purchaseOrder` 元素。  
  
6.  通过双击每个节点或单击每个节点右侧的双箭头，展开 `shipTo`、`billTo` 和 `items` 节点。  
  
     现在 `purchaseOrder` 元素的节点已展开，您可以查看元素的内容模型。  
  
7.  单击 `purchaseOrder` 元素下的任何节点并查看痕迹栏，以了解所选节点在架构集中的位置。  
  
8.  单击**显示文档**XSD 工具栏以切换文档中的按钮。 还可以右击设计图面来切换文档。  
  
9. 右击`purchaseOrder`节点，然后选择**生成示例 XML**若要查看 XML 实例文档。