---
title: "要添加到设计器中的对象使用的数据连接与设计器当前所用的数据连接不同 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 要添加到设计器中的对象使用的数据连接与设计器当前所用的数据连接不同
要添加到设计器中的对象使用的数据连接与设计器当前所用的数据连接不同。是否要替换设计器使用的连接?  
  
 在将项添加到[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)]（[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]）时，所有项都使用同一个共享数据连接。（设计图面表示 <xref:System.Data.Linq.DataContext>，它将单个连接用于图面上的所有对象。）如果添加到设计器中的对象使用的数据连接与设计器当前使用的数据连接不同，则会出现此消息。若要解决此错误，可以选择保持现有连接。如果选择这样做，则不会添加所选对象。您也可以选择添加对象并将 <xref:System.Data.Linq.DataContext> 连接重置为新的连接。  
  
> [!NOTE]
>  如果单击**“是”**，则 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上的所有实体类都映射到新连接。  
  
### 将现有连接替换为所选对象使用的连接  
  
-   单击**“是”**。  
  
     所选对象将添加到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中，并且 DataContext.Connection 设置为新连接。  
  
### 继续使用现有连接并取消添加所选对象的操作  
  
-   单击**“否”**。  
  
     操作被取消。DataContext.Connection 仍然设置为现有连接。  
  
## 请参阅  
 [对象关系设计器（O\/R 设计器）](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)