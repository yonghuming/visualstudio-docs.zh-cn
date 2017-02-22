---
title: "How to: Implement an Interface (Class Designer) | Microsoft Docs"
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
  - "interfaces [Visual Studio], implementing"
  - "interfaces [Visual Studio]"
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Implement an Interface (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在类设计器中，可以在类关系图上将接口连接至为接口方法提供代码的类，以此来实现接口。  类设计器可生成接口实现，并将接口与类之间的关系显示为继承关系。  您可以通过在接口与类之间绘制继承连线或从类视图拖动接口来实现接口。  
  
> [!TIP]
>  创建接口的方法与创建其他类型的方法相同。  如果接口存在但未显示在类关系图上，则首先要显示接口。  有关更多信息，请参见[How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md)和[How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md)。  
  
### 通过绘制继承连线实现接口  
  
1.  在类关系图上，显示接口和将实现该接口的类。  
  
2.  从类和接口绘制一条继承连线。  
  
     将有一个棒糖形附加在类上，还有一个带接口名称的标签，用以标识继承关系。  Visual Studio 为所有接口成员生成存根。  
  
 有关更多信息，请参见 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)。  
  
### 从“类视图”窗口实现接口  
  
1.  在类关系图上，显示要实现接口的类。  
  
2.  打开类视图并定位该接口。  
  
    > [!TIP]
    >  如果类视图尚未打开，则从**“视图”**菜单打开类视图。  有关类视图的更多信息，请参见 [Viewing Classes and Their Members](http://msdn.microsoft.com/zh-cn/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333)。  
  
3.  在关系图上将接口节点拖动至类形状。  
  
     将有一个棒糖形附加在类上，还有一个带接口名称的标签，用以标识继承关系。  Visual Studio 为所有接口成员生成存根；至此就实现了接口。  
  
## 请参阅  
 [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md)   
 [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md)   
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refactoring Classes and Types \(Class Designer\)](../ide/refactoring-classes-and-types-class-designer.md)