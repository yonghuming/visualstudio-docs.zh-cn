---
title: "CA1065：不要在意外的位置引发异常 | Microsoft Docs"
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
  - "CA1065"
  - "DoNotRaiseExceptionsInUnexpectedLocations"
helpviewer_keywords: 
  - "DoNotRaiseExceptionsInUnexpectedLocations"
  - "CA1065"
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1065：不要在意外的位置引发异常
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotRaiseExceptionsInUnexpectedLocations|  
|CheckId|CA1065|  
|类别|Microsoft.Design|  
|是否重大更改|否|  
  
## 原因  
 不应引发异常的方法引发了异常。  
  
## 规则说明  
 不应引发异常的方法可分为以下几类：  
  
-   Property Get 方法  
  
-   事件访问器方法  
  
-   Equals 方法  
  
-   GetHashCode 方法  
  
-   ToString 方法  
  
-   静态构造函数  
  
-   终结器  
  
-   Dispose 方法  
  
-   相等运算符  
  
-   隐式转换运算符  
  
 以下各节讨论这些方法类型。  
  
### Property Get 方法  
 属性基本上就是智能字段。  因此，它们在行为上应尽可能与字段类似。  字段不会引发异常，属性也不应引发异常。  如果您的属性引发异常，可以考虑将其变成一个方法。  
  
 允许从 Property Get 方法中引发下列异常：  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> 和所有派生对象（包括 <xref:System.ObjectDisposedException?displayProperty=fullName>）  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> 和所有派生对象  
  
-   <xref:System.ArgumentException?displayProperty=fullName>（仅从索引的 get 中）  
  
-   <xref:System.Collections.Generic.KeyNotFoundException>（仅从索引的 get 中）  
  
### 事件访问器方法  
 事件访问器应是不会引发异常的简单操作。  在您尝试添加或移除事件处理程序时，事件不应引发异常。  
  
 允许从事件访问器中引发下列异常：  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> 和所有派生对象（包括 <xref:System.ObjectDisposedException?displayProperty=fullName>）  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> 和所有派生对象  
  
-   <xref:System.ArgumentException> 和派生对象  
  
### Equals 方法  
 下列 **Equals** 方法不应引发异常：  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 **Equals** 方法应返回 `true` 或 `false`，而不是引发异常。  例如，如果向 Equals 传递了两个不匹配的类型，它应只返回 `false`，而不是引发 <xref:System.ArgumentException>。  
  
### GetHashCode 方法  
 下列 **GetHashCode** 方法通常不应引发异常：  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M:IEqualityComparer.GetHashCode\(T\)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode** 应始终返回一个值。  否则，哈希表中可能会丢失项。  
  
 采用参数的 **GetHashCode** 版本可以引发 <xref:System.ArgumentException>。  但是，**Object.GetHashCode** 永远都不应引发异常。  
  
### ToString 方法  
 调试器使用 <xref:System.Object.ToString%2A?displayProperty=fullName> 帮助按照字符串格式显示对象相关信息。  因此，**ToString** 不应更改对象的状态，也不应引发异常。  
  
### 静态构造函数  
 从静态构造函数中引发异常会导致类型无法在当前应用程序域中使用。  要从静态构造函数中引发异常，应该具有充足的理由（例如，出现安全问题）。  
  
### 终结器  
 从终结器中引发异常会导致 CLR 很快失败，从而使进程销毁。  因此，始终应避免在终结器中引发异常。  
  
### Dispose 方法  
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 方法不应引发异常。  Dispose 通常在 `finally` 子句中作为清理逻辑的一部分进行调用。  因此，从 Dispose 中显式引发异常将强制用户在 `finally` 子句中添加异常处理。  
  
 **Dispose\(false\)** 代码路径永远不应引发异常，因为它几乎总是从终结器中进行调用。  
  
### 相等运算符（\=\= 和 \!\=）  
 与 Equals 方法类似，相等运算符应返回 `true` 或 `false`，而不应引发异常。  
  
### 隐式转换运算符  
 因为用户通常不知道调用了隐式转换运算符，所以隐式转换运算符引发的异常完全出乎意料。  因此，不应从隐式转换运算符中引发异常。  
  
## 如何解决冲突  
 对于属性 getter，可以更改逻辑使其不再需要引发异常，或者将该属性更改为方法。  
  
 对于前面列出的所有其他方法类型，可以更改逻辑使其不再需要引发异常。  
  
## 何时禁止显示警告  
 如果冲突是由于异常声明引起而不是由于引发的异常引起，则可以放心地禁止显示此规则发出的警告。  
  
## 相关规则  
 [CA2219：在异常子句中不引发异常](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)  
  
## 请参阅  
 [设计警告](../code-quality/design-warnings.md)