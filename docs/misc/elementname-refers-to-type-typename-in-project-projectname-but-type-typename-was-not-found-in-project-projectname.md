---
title: "“&lt;elementname&gt;”引用项目“&lt;projectname&gt;”中的类型“&lt;typename&gt;”，但在项目“&lt;projectname&gt;”中找不到类型“&lt;typename&gt;” | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30960"
  - "bc30960"
helpviewer_keywords: 
  - "BC30960"
ms.assetid: 4ed4bff5-c670-46f6-8360-7287444d50e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;elementname&gt;”引用项目“&lt;projectname&gt;”中的类型“&lt;typename&gt;”，但在项目“&lt;projectname&gt;”中找不到类型“&lt;typename&gt;”
某表达式将访问另一项目中引用的类、结构、模块或接口，但该项目不包含指定的类型。  
  
 当项目间接引用同一解决方案中的另一个项目时，将发生此错误。 通常情况下，项目引用一个程序集，该程序集引用另一个项目。 如果该程序集访问另一个项目中的指定类型，则建立了对该类型的间接引用。 但是，如果另一个项目中不存在此类型，则会产生此错误。  
  
 **错误 ID：**BC30960  
  
### 更正此错误  
  
-   如果所引用类型在任何位置都不再有定义，请删除或替换尝试访问它的语句。 可能还需要对间接引用了被引用类型的程序集进行相同更改。  
  
-   如果在某一位置定义了引用类型，请对定义它的项目或程序集进行直接引用。  
  
## 请参阅  
 [NIB：引用命名空间和组件](http://msdn.microsoft.com/zh-cn/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [管理项目中的引用](../ide/managing-references-in-a-project.md)   
 [NIB：管理引用](http://msdn.microsoft.com/zh-cn/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB 如何：使用“添加引用”对话框添加或删除引用](http://msdn.microsoft.com/zh-cn/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)