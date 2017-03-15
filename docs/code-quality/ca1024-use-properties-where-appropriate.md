---
title: "CA1024：在适用处使用属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePropertiesWhereAppropriate"
  - "CA1024"
helpviewer_keywords: 
  - "CA1024"
  - "UsePropertiesWhereAppropriate"
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1024：在适用处使用属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|UsePropertiesWhereAppropriate|  
|CheckId|CA1024|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 公共或受保护方法的名称以 `Get` 开头，没有采用任何参数或返回的值不是数组。  
  
## 规则说明  
 在大多数情况下，属性代表数据，而方法执行操作。  访问属性的方式与访问字段的方式相似，因此使用它们更容易。  如果存在下列条件之一，方法就很适于成为属性：  
  
-   不采用任何参数并返回对象的状态信息。  
  
-   接受单个参数来设置对象的部分状态。  
  
 属性的表现应当与字段一样；如果该方法不是这样，则不应将其更改为属性。  在下列情况下，方法比属性更好：  
  
-   方法执行耗时的操作。  与设置或获取字段值所需的时间相比，此方法的速度明显较慢。  
  
-   方法执行转换。  访问字段不会返回它所存储的数据的转换版本。  
  
-   Get 方法会产生明显副作用。  检索字段的值不会产生任何副作用。  
  
-   执行的顺序很重要。  设置字段的值并不依赖于其他操作的发生。  
  
-   连续调用两次方法会产生不同的结果。  
  
-   方法是静态的，但返回了调用方可更改的对象。  调用方不能通过检索某字段的值来更改该字段存储的数据。  
  
-   方法返回数组。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将方法更改为属性。  
  
## 何时禁止显示警告  
 如果方法至少满足上文中列出的一个条件，则禁止显示与该规则有关的警告。  
  
## 在调试器中控制属性扩展  
 程序员避免使用属性的一个原因，是他们不希望调试器自动展开属性。  例如，属性可能涉及分配一个大型对象或调用 P\/Invoke，但它实际上可能不具有任何明显的副作用。  
  
 通过应用 <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName> 可以阻止调试器自动展开属性。  下面的示例演示如何将此特性应用到实例属性。  
  
```vb  
Imports System   
Imports System.Diagnostics   
  
Namespace Microsoft.Samples   
  
    Public Class TestClass   
  
        ' [...]   
  
        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _   
        Public ReadOnly Property LargeObject() As LargeObject   
            Get   
                ' Allocate large object   
                ' [...]   
            End Get   
        End Property   
  
    End Class   
  
End Namespace  
```  
  
```c#  
  
        using System;   
using System.Diagnostics;   
  
namespace Microsoft.Samples   
{   
    public class TestClass   
    {   
        // [...]   
  
        [DebuggerBrowsable(DebuggerBrowsableState.Never)]   
        public LargeObject LargeObject   
        {   
            get   
            {   
                // Allocate large object   
                // [...]   
  
        }  
    }  
}  
```  
  
## 示例  
 下面的示例包含多个应转换为属性的方法，还包含多个由于表现与字段不同而不应转换的方法。  
  
 [!code-cs[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]