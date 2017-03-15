---
title: "无法删除属性 &lt;属性名称&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# 无法删除属性 &lt;属性名称&gt;
无法删除属性 \<属性名称\>，因为它被设置为用于 \<类名称\> 和 \<类名称\> 之间的继承的鉴别器属性  
  
 选择的属性被设置为**“鉴别器属性”**，用于错误消息中所指示的类之间的继承。如果属性参与数据类之间的继承配置，则无法删除这些属性。  
  
 将**“鉴别器属性”**设置为数据类的另一个属性，可以成功删除希望删除的属性。  
  
### 更正此错误  
  
1.  在 O\/R 设计器中选择连接错误消息中指示的数据类的继承连线。  
  
2.  将**“鉴别器”**属性设置为另一个属性。  
  
3.  再次尝试删除该属性。  
  
## 请参阅  
 [如何：使用 O\/R 设计器配置继承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [数据类继承（O\/R 设计器）](../data-tools/data-class-inheritance-o-r-designer.md)   
 [演练：使用单表继承创建 LINQ to SQL 类（O\/R 设计器）](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)