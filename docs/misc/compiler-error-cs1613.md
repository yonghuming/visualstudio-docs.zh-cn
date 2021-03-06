---
title: "编译器错误 CS1613 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1613"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1613"
ms.assetid: 9d7ea9c8-9953-459f-a3f0-c7e65d1b9f59
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1613
找不到用于接口 “interface” coclass 包装类 “class” （是否缺少程序集引用？）  
  
 已尝试实例化来自接口的 COM 对象。 此接口具有 **ComImport** 和 `CoClass` 特性，但编译器找不到为 `CoClass` 特性给定的类型。  
  
 要解决此错误，你可以尝试以下项之一：  
  
-   向具有 coclass 的程序集添加一个引用（大多数情况下，接口和 coclass 应位于同一程序集中） 请参阅[\/引用](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)或[添加引用对话框](http://msdn.microsoft.com/zh-cn/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)获取信息。  
  
-   修复接口上的 `CoClass` 特性。  
  
 以下示例演示如何正确使用 **CoClassAttribute**：  
  
```  
// CS1613.cs using System; using System.Runtime.InteropServices; [Guid("1FFD7840-E82D-4268-875C-80A160C23296")] [ComImport()] [CoClass(typeof(A))] public interface IA{} public class A : IA {} public class AA { public static void Main() { IA i; i = new IA(); // This is equivalent to new A(). // because of the CoClass attribute on IA } }  
```