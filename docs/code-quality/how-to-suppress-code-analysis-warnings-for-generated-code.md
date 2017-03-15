---
title: "如何：禁止显示所生成代码的代码分析警告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：禁止显示所生成代码的代码分析警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

托管代码编译器通常会生成一些代码添加到项目中，以加快代码的开发。  此外，开发人员通常使用第三方工具加快应用程序的开发。  这些工具还会生成一些代码添加到项目中。  
  
 您可能希望看到代码分析在所生成代码中发现的规则冲突。  但是，如果不能查看和维护包含冲突的代码，您可能不会看到规则冲突。  
  
 通过项目的“代码分析”属性页上的**“禁止显示所生成代码的结果”**复选框，可以选择是否看到第三方工具生成的代码的代码分析警告。  
  
> [!NOTE]
>  当所生成代码中的代码分析错误和警告出现在窗体和模板中时，此选项不会禁止显示它们。  可以查看和维护窗体或模板的源代码。  
  
### 禁止显示项目中所生成代码的警告  
  
1.  在“解决方案资源管理器”中右击相应项目，然后单击**“属性”**。  
  
2.  单击**“代码分析”**。  
  
3.  选中**“禁止显示所生成代码的结果”**复选框。