---
title: "编译器警告（等级 1）CS3010 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3010"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3010"
ms.assetid: d57bd750-df15-4e6a-9579-66de8b276b7e
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器警告（等级 1）CS3010
“member”：符合 CLS 的接口必须仅有符合 CLS 的成员  
  
 在具有 `[assembly:CLCSompliant(true)]` 标记的程序集中，接口包含具有 `[CLCSompliant(false)]` 标记的成员。 删除其中一个共用语言规范 \(CLS\) 遵从性特性。 有关 CLS 遵从性的详细信息，请参阅 [\<PAVE OVER\> 编写符合 CLS 的代码](http://msdn.microsoft.com/zh-cn/4c705105-69a2-4e5e-b24e-0633bc32c7f3)和 [语言独立性和与语言无关的组件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  
  
## 示例  
 下面的示例生成 CS3010：  
  
```  
// CS3010.cs using System; [assembly:CLSCompliant(true)] public interface I { [CLSCompliant(false)] int M();   // CS3010 } public class C : I { public int M() { return 1; } public static void Main() { } }  
```