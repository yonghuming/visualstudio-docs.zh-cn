---
title: "How to: Create Inheritance Between Types (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.inheritanceline"
helpviewer_keywords: 
  - "inheritance, relationship defining"
  - "relationships, defining inheritance"
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# How to: Create Inheritance Between Types (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要使用类设计器在类图上的两种类型之间创建继承关系，请将基类型与其派生的类型相连接。  你可以有存在于两个类之间、类和接口之间，或者是两个接口之间的继承关系。  
  
### 在类型之间创建继承  
  
1.  从解决方案资源管理器中的项目打开一个类图 \(.cd\) 文件。  
  
     如果你尚未拥有类图，请创建一个。  请参阅[How to: Add Class Diagrams to Projects \(Class Designer\)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)。  
  
2.  在**“工具箱”**的**“类设计器”**下，单击**“继承”**。  
  
3.  在类关系图上，在你想要的两个类型之间绘制一条继承连线，从:  
  
    -   派生类到基类  
  
    -   实现类到已实现接口  
  
    -   扩展接口到已扩展接口  
  
4.  （可选）当你有从泛型类型派生的类型时，单击该继承连线。  在**“属性”**窗口中，设置**“类型参数”**属性以匹配你想要用于泛型类型的类型。  
  
    > [!NOTE]
    >  如果父抽象类至少包含一个抽象成员，则所有这些成员都将作为非抽象的继承类实现。  请参阅[Implementing Abstract Base Classes](../ide/refactoring-classes-and-types-class-designer.md#ImplementingAbstractBaseClasses)。  
    >   
    >  尽管可对现有泛型类型进行可视化，但不能创建新的泛型类型。  还不能更改现有泛型类型的类型参数。  
  
## 请参阅  
 [继承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)   
 [继承的基础知识](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [How to: View Inheritance Between Types \(Class Designer\)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Visual C\+\+ Classes in Class Designer](../ide/visual-cpp-classes-in-class-designer.md)