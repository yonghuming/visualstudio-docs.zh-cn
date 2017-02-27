---
title: "How to: Add Class Diagrams to Projects (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "class diagrams, creating"
  - "Class Designer [Visual Studio], opening"
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# How to: Add Class Diagrams to Projects (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要设计、编辑及重构类和其他类型，请将类图添加到 Visual C\# .NET、Visual Basic .NET 或 C\+\+ 项目中。  若要直观显示项目中代码的不同部分，请将多个类图添加到该项目中。  
  
 你不可以从在多个应用间共享代码的项目创建类图。  要创建 UML 类图，请参阅[创建 UML 建模项目和关系图](../modeling/create-uml-modeling-projects-and-diagrams.md)。  
  
### 向项目中添加空白类图  
  
1.  在解决方案资源管理器中，右击项目名称。  然后选择**“添加新项”**或**“添加”**\-\>**“新建项”**。  
  
2.  从模板列表中选择**“类图”**。  对于 Visual C\+\+ 项目，请查看**“模板”**下方，然后查看**“实用工具”**下方以查找该模板。  
  
     类图随即在类设计器中打开，并在解决方案资源管理器的项目层次结构中以一个带 .cd 扩展名的文件出现。  使用“类设计器”工具箱将形状和线条拖动到类图中。  
  
3.  要添加多个类图，请重复上述步骤。  
  
### 基于现有类型添加类图  
  
1.  在解决方案资源管理器中，打开类文件上下文菜单，然后选择**“查看类图”**。  
  
     \- 或 \-  
  
     在**“类视图”**中，打开命名空间或类型上下文菜单，然后选择**“查看类图”**。  
  
### 在类图中显示完整项目的内容  
  
1.  在解决方案资源管理器或“类视图”中，右键单击项目并选择**“查看”**，然后选择**“查看类图”**。  
  
     即会创建一个自动填充的类图。  
  
## 请参阅  
 [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md)   
 [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md)   
 [Designing Classes and Types \(Class Designer\)](../ide/designing-classes-and-types-class-designer.md)   
 [Viewing Types and Relationships \(Class Designer\)](../ide/viewing-types-and-relationships-class-designer.md)   
 [Working with Class Diagrams \(Class Designer\)](../ide/working-with-class-diagrams-class-designer.md)