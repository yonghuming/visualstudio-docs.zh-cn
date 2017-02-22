---
title: "排序、筛选和分组（XML 架构资源管理器） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 排序、筛选和分组（XML 架构资源管理器）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍通过 XML 架构资源管理器工具栏上的**“排序、筛选和分组选项”**菜单可用的选项。  
  
## 筛选器选项  
 下列筛选器选项可用。默认情况下，**“显示命名空间”**和**“显示架构文件”**选项处于选中状态。  
  
-   **显示命名空间**。  
  
-   **显示架构文件**。  
  
-   **显示排序器 \(sequence\/choice\/all\)**。  
  
## 排序选项  
 下列排序选项可用。默认为**“按类型排序”**。“排序方式”选项不适用于文件和命名空间。  
  
-   **按类型排序**。  
  
-   **按名称排序**。  
  
-   **文档顺序**.  
  
### 按类型排序  
 选中**“按类型排序”**选项后，全局节点将按以下顺序进行排序。然后，在每个组中，节点将按字母顺序进行排序。  
  
1.  `import` 节点。  
  
2.  `include` 节点。  
  
3.  `redefine` 节点。  
  
4.  `attribute` 节点。  
  
5.  `attributeGroup` 节点。  
  
6.  `complexType` 节点。  
  
7.  `simpleType` 节点。  
  
8.  `element` 节点。  
  
9. `group` 节点。  
  
### 按名称排序  
 选中**“按名称排序”**选项后，全局节点将按以下顺序进行排序：  
  
1.  `import` 节点（按命名空间的字母顺序）。  
  
2.  `include` 节点（按 `schemaLocation` 特性的字母顺序）。  
  
3.  `redefine` 节点（按 `schemaLocation` 特性的字母顺序）。  
  
4.  其他全局节点（按字母顺序）。  
  
### 文档顺序  
 选中**“显示架构文件”**选项后，**“文档顺序”**选项将变为可用。选中**“文档顺序”**后，全局节点的显示顺序将与其在架构文件中的显示顺序相同。  
  
## 保留排序\/筛选器选项  
 无论更改设置时打开的是哪个解决方案或文件，排序、筛选和分组选项均会保存到每个用户的注册表中。