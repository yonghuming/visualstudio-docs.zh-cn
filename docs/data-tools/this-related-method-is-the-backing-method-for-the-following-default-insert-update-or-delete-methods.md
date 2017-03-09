---
title: "此相关方法是下列默认插入、更新或删除方法的备份方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 此相关方法是下列默认插入、更新或删除方法的备份方法
此相关方法是下列默认插入、更新或删除方法的备份方法。如果删除这些方法，则备份方法也将被删除。是否要继续?  
  
 所选的 `DataContext` 方法当前用作 O\/R 设计器上某实体类的插入、更新或删除方法之一。如果删除所选方法，则使用此方法的实体类在更新过程中执行插入、更新或删除时将还原为默认的运行时行为。  
  
### 删除所选方法，使实体类使用运行时更新  
  
-   单击**“是”**。  
  
     所选方法将被删除，并且使用此方法重写更新行为的所有类将还原为使用默认 LINQ to SQL 运行时行为。  
  
### 关闭消息框，不对所选方法进行更改  
  
-   单击**“否”**。  
  
     消息框关闭，不进行任何更改。  
  
## 请参阅  
 [DataContext 方法（O\/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)   
 [如何：分配存储过程以执行更新、插入和删除（O\/R 设计器）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [O\/R 设计器概述](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)