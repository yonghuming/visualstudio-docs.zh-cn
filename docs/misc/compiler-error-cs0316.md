---
title: "编译器错误 CS0316 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0316"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0316"
ms.assetid: 8b70abbe-dd4f-473f-8dfe-f8309abef276
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0316
参数名“name”与某个自动生成的参数名冲突。  
  
 保留的字不能用作参数名。 在以下示例中，`value` 是默认属性或索引器访问器上下文中的保留字。  
  
### 更正此错误  
  
1.  更改参数的名称。  
  
## 示例  
 以下代码生成 CS0316：  
  
```  
// cs0316.cs // Compile with: /target:library public class Test { public int this[int value] // CS0316 { get { return 1; } set { } } }  
```  
  
## 请参阅  
 [索引器](/dotnet/csharp/programming-guide/indexers/index)   
 [C\# 关键字](/dotnet/csharp/language-reference/keywords/index)