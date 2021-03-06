---
title: "特性说明符不是一个完整的语句 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32035"
  - "bc32035"
helpviewer_keywords: 
  - "BC32035"
ms.assetid: a0ddd673-4170-4bea-9c22-777d7bf21dfd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 特性说明符不是一个完整的语句
特性说明符不是一个完整的语句。 请使用续行符将该特性应用于下列语句。  
  
 在源代码行上单独显示特性块。 特性必须应用在声明语句开头，并且它们必须是该语句的一部分。  
  
 **错误 ID：**BC32035  
  
### 更正此错误  
  
-   如果声明语句在下一行，则在特性块后面添加一个空格和一条下划线 \(`_`\) 以结合源代码行。  
  
-   如果没有声明语句与该特性块相关联，请提供一个声明语句或删除该特性块。  
  
-   如果该特性将应用于整个程序集或当前程序集模块，特性块将保留在单独的源代码行上。 将 `Assembly:` 或 `Module:` 置于尖括号内的特性名称 \(`< >`\) 之前，且不可在特性块之后添加空格或下划线。 此外，请确保该特性块位于你的源文件开头。  
  
## 请参阅  
 [不在生成中：特性的应用程序](http://msdn.microsoft.com/zh-cn/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [如何：在代码中拆分和合并语句](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)