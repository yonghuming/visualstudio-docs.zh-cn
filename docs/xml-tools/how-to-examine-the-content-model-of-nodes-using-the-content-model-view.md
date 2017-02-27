---
title: "如何：使用内容模型视图检查节点的内容模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 如何：使用内容模型视图检查节点的内容模型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题描述如何使用[内容模型视图](../xml-tools/content-model-view.md)浏览节点。  
  
### 创建新的 XSD 文件并显示内容模型视图中的根元素  
  
1.  创建新的 XML 架构文件。  
  
2.  在起始视图上，单击**“使用 XML 编辑器查看和编辑基础 XML 架构文件”**。  
  
3.  从[示例 XML 架构：订单架构](../Topic/Sample%20XSD%20File:%20Purchase%20Order%20Schema.md)复制并粘贴 XML 架构示例代码，以替换默认情况下添加到新 XSD 文件的代码。  
  
4.  通过右击 XML 编辑器中的 `purchaseOrder` 元素并选择**“在 XML 架构资源管理器中显示”**，在架构资源管理器中选择 `purchaseOrder` 元素。  
  
5.  右击 XML 资源管理器中的 `purchaseOrder`，并选择**“在内容模型视图中显示”**。  
  
     内容模型视图显示设计图面上的 `purchaseOrder` 元素。  
  
6.  通过双击每个节点或单击每个节点右侧的双箭头，展开 `shipTo`、`billTo` 和 `items` 节点。  
  
     现在 `purchaseOrder` 元素的节点已展开，您可以查看元素的内容模型。  
  
7.  单击 `purchaseOrder` 元素下的任何节点并查看痕迹栏，以了解所选节点在架构集中的位置。  
  
8.  单击 XSD 工具栏中的**“显示文档”**按钮以切换文档。还可以右击设计图面来切换文档。  
  
9. 右击 `purchaseOrder` 节点并选择**“生成示例 XML”**可查看 XML 实例文档。