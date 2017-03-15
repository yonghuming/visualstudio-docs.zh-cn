---
title: "CA1409：Com 可见类型应该是可创建的 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
helpviewer_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1409：Com 可见类型应该是可创建的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|类别|Microsoft.Interoperability|  
|是否重大更改|非重大更改|  
  
## 原因  
 专门标记为对组件对象模型 \(COM\) 可见的某个引用类型包含公共的参数化构造函数，但不包含公共的默认（无参数）构造函数。  
  
## 规则说明  
 没有公共默认构造函数的类型不能由 COM 客户端创建。  但是，如果可以使用其他方法创建该类型并将它传递到客户端（例如，通过某个方法调用的返回值），则 COM 客户端仍然可以访问该类型。  
  
 该规则忽略从 <xref:System.Delegate?displayProperty=fullName> 派生的类型。  
  
 默认情况下，以下项对 COM 可见：程序集、公共类型、公共类型中的公共实例成员和公共值类型的所有成员。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请添加公共的默认构造函数或者从类型中移除 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>。  
  
## 何时禁止显示警告  
 如果提供了其他方法来创建对象并将对象传递到 COM 客户端，则可以安全地禁止显示此规则发出的警告。  
  
## 相关规则  
 [CA1017：用 ComVisibleAttribute 标记程序集](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## 请参阅  
 [为互操作限定 .NET 类型](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [与非托管代码交互操作](../Topic/Interoperating%20with%20Unmanaged%20Code.md)