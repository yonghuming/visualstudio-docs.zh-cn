---
title: "局部变量不能与包含它的函数同名 | Microsoft Docs"
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
  - "vbc30290"
  - "bc30290"
helpviewer_keywords: 
  - "BC30290"
ms.assetid: 34c38cff-fb9c-406d-82e8-ca251ee77104
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 局部变量不能与包含它的函数同名
`Dim` 语句指定的某个变量与包含该变量的 `Function` 过程同名。  
  
 **错误 ID：**BC30290  
  
### 更正此错误  
  
-   删除变量声明，或更改变量的名称。  
  
## 请参阅  
 [NOTINBUILD：当多个变量具有相同名称时解析引用](http://msdn.microsoft.com/zh-cn/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [Function 过程](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)