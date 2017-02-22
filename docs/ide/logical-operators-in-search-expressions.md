---
title: "搜索表达式中的逻辑运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Help Viewer 2.0，搜索中的逻辑运算符"
  - "搜索中的逻辑运算符 [Help Viewer 2.0]"
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 搜索表达式中的逻辑运算符
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用逻辑搜索运算符，则可以通过创建从较简单类型而来的复杂的搜索表达式改善搜索内容。  如下表所示，逻辑运算符指定如何在搜索查询使用多个搜索词。  
  
> [!IMPORTANT]
>  您必须为搜索引擎输入全是大写字母的逻辑运算符以便识别它们。  
  
|要搜索的|使用|示例|结果|  
|----------|--------|--------|--------|  
|在同一主题中的两个术语|AND|dib AND 调色板|包含“dib”和“调色板”的主题。|  
|主题中的任何一个术语|OR|光栅 OR 矢量|包含“光栅”或“矢量”的主题。|  
|在同一主题中一个术语无二意|NOT|“操作系统” NOT DOS|包含“操作系统”而不是“DOS”的主题。|  
|两个术语，有同一主题|NEAR|NEAR 用户|“核心”接近程度中包含“用户”的主题。|  
  
## 请参阅  
 [全文搜索提示](../ide/full-text-search-tips.md)   
 [找到信息](../ide/locate-information.md)