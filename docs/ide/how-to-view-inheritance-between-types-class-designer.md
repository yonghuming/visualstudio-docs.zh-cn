---
title: "How to: View Inheritance Between Types (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.AssociationTypeNotFoundError"
helpviewer_keywords: 
  - "types [Visual Studio], inheritance"
  - "types [Visual Studio], base"
  - "types [Visual Studio], derived"
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: View Inheritance Between Types (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果基类型和派生类型之间存在继承关系，则可在类设计器中的类关系图上查看这种关系。  如果这两种类型之间不存在继承关系，则请参阅[How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)以创建继承关系。  
  
### 查找基类型  
  
1.  在类关系图中，单击要查看基类或基接口的类型。  
  
2.  在**“类关系图”**菜单中，选择**“显示基类”**或**“显示基接口”**。  
  
     类型的基类或基接口在关系图中显示为选中状态。  原来隐藏的所有继承连线现在都会出现在两个形状之间。  
  
 你还可以右击想要显示其基类型的类型，再选择**“显示基类”**或**“显示基接口”**。  
  
### 查找派生类型  
  
1.  在类关系图中，单击要查看派生类或派生接口的类型。  
  
2.  在**“类关系图”**菜单中，选择**“显示派生类”**或**“显示派生接口”**。  
  
     该类型的派生类或派生接口即会出现在关系图中。  原来隐藏的所有继承连线现在都会出现在形状之间。  
  
 你还可以右击想要显示其派生类型的类型，再选择**“显示派生类”**或**“显示派生接口”**。  
  
## 请参阅  
 [How to: Create Associations Between Types \(Class Designer\)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Viewing Types and Relationships \(Class Designer\)](../ide/viewing-types-and-relationships-class-designer.md)