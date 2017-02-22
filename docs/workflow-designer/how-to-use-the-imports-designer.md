---
title: "如何：使用导入设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.ImportDesigner.UI"
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 如何：使用导入设计器
导入设计器允许您为将在表达式中使用的类型输入命名空间。与 Visual Basic .NET 和 C\# 中的 **Imports** 或 **using** 关键字非常类似，在导入设计器中指定命名空间使您在表达式中只需输入类型名称，而不是完全限定的版本类型名称。  
  
 导入设计器既响应 UI 中的更改，也响应保存工作流时进行的更改。保存工作流后，会向导入设计器中自动添加命名空间。其中包括：  
  
-   变量和参数声明中使用的所有类型的命名空间。  
  
-   表达式中使用的所有类型的命名空间。  
  
-   序列化工作流所需的其他任何命名空间（例如，放置在工作流中的自定义活动所使用的命名空间）。  
  
 保存工作流时，您可能会注意到您已手动删除的某些命名空间可能会由于上述列表中描述的逻辑自动重新添加到导入设计器中。  
  
### 向导入的命名空间列表中添加命名空间  
  
1.  在 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 或重新承载的工作流应用程序中，打开一个 WCF 工作流服务应用程序、工作流控制台应用程序或活动库项目。  
  
2.  单击主画布底部的**“导入”**。此时将显示导入设计器。  
  
3.  输入或从导入设计器顶部的下拉列表控件中选择一个命名空间。  
  
     您键入时，会显示与键入的字符匹配的有效命名空间列表。  
  
4.  按 **Enter** 键将该命名空间添加到列表中。  
  
5.  如果您想从列表中移除某个命名空间，请选择该命名空间，然后按键盘上的 **Delete** 键。请注意是否命名空间无效因任何理由，例如如果由项目不再引用程序集，其中包含命名空间，可以只删除命名空间。