---
title: "无法删除属性 &lt;属性名称&gt;，原因是它参与了关联 &lt;关联名称&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 无法删除属性 &lt;属性名称&gt;，原因是它参与了关联 &lt;关联名称&gt;
选择的属性被设置为错误消息中指示的类之间关联的**“关联属性”**。如果属性参与了数据类之间的关联，则无法删除。  
  
 将**“关联属性”**设置为数据类的另一个属性，可以成功删除希望删除的属性。  
  
### 更正此错误  
  
1.  在 O\/R 设计器中选择连接错误消息中指示的数据类的关联连线。  
  
2.  双击该连线以打开**“关联编辑器”**对话框。  
  
3.  从**“关联属性”**中移除该属性。  
  
4.  再次尝试删除该属性。  
  
## 请参阅  
 [O\/R 设计器概述](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [如何：创建 LINQ to SQL 类之间的关联（关系）（O\/R 设计器）](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [演练：创建 LINQ to SQL 类（O\/R 设计器）](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)