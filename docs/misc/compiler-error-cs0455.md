---
title: "编译器错误 CS0455 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0455"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0455"
ms.assetid: a09840ac-ad8c-4c9c-868e-b83d937c7047
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0455
类型参数“Type Parameter Name”继承冲突的约束 \-“约束名称 1”和“约束名称 2”  
  
 获得此错误的两种常见方式是设置约束，使类型参数派生自两个不相关的类，或者使它派生自类类型或引用类型约束和 `struct` 类型或值类型约束。 若要解决此错误，请从继承层次结构中删除冲突。  
  
## 示例  
 以下代码生成错误 CS0455。  
  
```  
// CS0455.cs using System; public class GenericsErrors { public class B { } public class B2 { } public class G6<T> where T : B { public class N<U> where U : B2, T { } } // CS0455 }  
```