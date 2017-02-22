---
title: "如何：从图形视图和内容模型视图打印关系图 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e1785e4-4aaf-4c66-8735-51e7ca035565
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：从图形视图和内容模型视图打印关系图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题描述如何从图形视图或内容模型视图中打印关系图。  
  
### 从 XML 架构设计器中打印关系图  
  
1.  在 Visual Studio 中打开 XSD 文件并且将某些节点添加到 [XML 架构设计器工作区](../xml-tools/xml-schema-designer-workspace.md)。  
  
2.  通过使用图形视图或内容模型视图的设计图面中的**“将关系图导出为图像...”**上下文菜单项，将关系图导出到 XPS 文件。  
  
     当您从图形视图导出关系图时，整个设计图面将被导出到 XPS 文件。当您从内容模型视图导出关系图，并且多个节点显示在内容模型视图的设计图面上时，只有第一节点会导出到 XPS 文件。  
  
3.  通过使用 XPS 查看器，打印在 XPS 文件中保存的图像。  
  
## 请参阅  
 [图形视图](../xml-tools/graph-view.md)   
 [内容模型视图](../xml-tools/content-model-view.md)   
 [XML 架构设计器工作区](../xml-tools/xml-schema-designer-workspace.md)