---
title: "更改 DataContext 方法的返回类型的操作无法撤消 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 更改 DataContext 方法的返回类型的操作无法撤消
更改 DataContext 方法的返回类型的操作无法撤消。要恢复为自动生成的类型，您必须将该项从服务器资源管理器\/数据库资源管理器中再次拖动到 O\/R Designer 上。是否确实要更改返回类型？  
  
 <xref:System.Data.Linq.DataContext> 方法的返回类型根据您在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中放置项的位置而不同。如果直接将项放在现有实体类上，则将创建具有该实体类返回类型的 <xref:System.Data.Linq.DataContext> 方法。如果将项放在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白区域，则将创建返回自动生成类型的 <xref:System.Data.Linq.DataContext> 方法。在将 <xref:System.Data.Linq.DataContext> 方法添加到方法窗格后可以更改该方法的返回类型。若要检查或更改 <xref:System.Data.Linq.DataContext> 方法的返回类型，请选中该方法并在**“属性”**窗口中单击**“返回类型”**属性。  
  
### 更改 DataColumn 的返回类型  
  
-   单击**“是”**。  
  
### 退出消息框，不更改返回类型  
  
-   单击**“否”**。  
  
### 在更改返回类型后恢复为原始返回类型  
  
1.  在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上选择 <xref:System.Data.Linq.DataContext> 方法，然后删除它。  
  
2.  在**“服务器资源管理器\/数据库资源管理器”**中找到该项，并将其拖动到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上。  
  
     这样做将创建具有原始默认返回类型的 <xref:System.Data.Linq.DataContext> 方法。  
  
## 请参阅  
 [对象关系设计器（O\/R 设计器）](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext 方法（O\/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)   
 [如何：创建映射到存储过程和函数的 DataContext 方法（O\/R 设计器）](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)