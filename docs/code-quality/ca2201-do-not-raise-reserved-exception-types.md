---
title: "CA2201：不要引发保留的异常类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotRaiseReservedExceptionTypes"
  - "CA2201"
helpviewer_keywords: 
  - "CA2201"
  - "DoNotRaiseReservedExceptionTypes"
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2201：不要引发保留的异常类型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|类别|Microsoft.Usage|  
|是否重大更改|是|  
  
## 原因  
 某方法引发的异常类型过于一般或者是运行时保留的类型。  
  
## 规则说明  
 下面的异常类型过于一般，不能向用户提供足够信息：  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 下面的异常类型是保留类型，仅应由公共语言运行时引发：  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **不要引发一般异常**  
  
 如果引发一般异常类型（例如库或框架中的 <xref:System.Exception> 或 <xref:System.SystemException>），则会强制使用者捕捉所有异常，包括使用者不知如何处理的未知异常。  
  
 应引发框架中已存在的派生程度更高的类型，或创建从 <xref:System.Exception> 派生的自己的类型。  
  
 **引发特定的异常**  
  
 下表列出了参数和验证这些参数将引发的异常，包括属性的 set 访问器中的 value 参数。  
  
|参数说明|异常|  
|----------|--------|  
|`null` 引用|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|超出值的允许范围（例如集合或列表的索引）|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|无效的 `enum` 值|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|包含的格式不符合方法的参数规范（例如 `ToString(String)` 的格式字符串）|<xref:System.FormatException?displayProperty=fullName>|  
|其他无效情况|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 当操作对对象的当前状态无效时   引发 <xref:System.InvalidOperationException?displayProperty=fullName>  
  
 对已释放的对象执行操作时   引发 <xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 当操作不受支持（例如，在打开用于读取的 Stream 中重写 **Stream.Write**）时   引发 <xref:System.NotSupportedException?displayProperty=fullName>  
  
 转换会导致溢出（例如，显式强制转换运算符重载）时   引发 <xref:System.OverflowException?displayProperty=fullName>  
  
 对于所有其他情形，请考虑创建从 <xref:System.Exception> 派生的自己的类型并引发该异常。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将引发的异常类型更改为不是保留类型之一的特定类型。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 相关规则  
 [CA1031：不要捕捉一般异常类型](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)