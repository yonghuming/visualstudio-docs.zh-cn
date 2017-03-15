---
title: "域路径语法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "域特定语言, 域路径"
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 25
---
# 域路径语法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DSL 定义使用类似 XPath 的语法在模型中查找特定元素。  
  
 通常，你不必直接使用此语法。  在“DSL 详细信息”或“属性”窗口中，你可以在它所显示的位置中单击向下箭头并使用路径编辑器。  但是，在使用编辑器后，该路径将以此形式显示在字段中。  
  
 域路径采用以下形式：  
  
 *RelationshipName.PropertyName\/\!Role*  
  
 ![CommentReferencesSubjects 引用关系](../modeling/media/dsl_reference.png "dsl\_reference")  
  
 该语法将遍历模型树。  例如，上图中的域关系 CommentReferencesSubjects 具有使用者角色。  路径段 \/\!Subjectt 将指定路径结束于通过使用者角色访问的元素。  
  
 每段都以域关系的名称开头。  如果从元素遍历到关系，则路径段将显示为 *Relationship.PropertyName*。  如果从链接跳跃到元素，则路径段将显示为 *Relationship\/\!RoleName*。  
  
 使用斜杠分隔路径的语法。  每个路径段是都从元素到链接（关系的实例）或从链接到元素的跳跃。  路径段经常成对显示。  一个路径段表示从元素到链接的跳跃，而下一个段则表示从链接到另一端的元素的跳跃。  （任何链接还可以是关系本身的源或目标）。  
  
 用于元素到链接跳跃的名称是角色的 `Property Name` 的值。  用于链接到元素跳跃的名称是目标角色名称。  
  
## 请参阅  
 [了解模型、类和关系](../modeling/understanding-models-classes-and-relationships.md)