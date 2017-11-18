---
title: "CA1024： 在适用处使用属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 42fb569dbf469ed91f96b25818b717353d53bf0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024：在适用处使用属性
|||  
|-|-|  
|TypeName|UsePropertiesWhereAppropriate|  
|CheckId|CA1024|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护的方法已开头的名称`Get`，没有采用任何参数并返回一个值，不是数组。  
  
## <a name="rule-description"></a>规则说明  
 在大多数情况下，属性表示数据和方法可执行操作。 像字段，它们可以更轻松地使用一样访问属性。 一种方法是适于成为属性，如果以下条件之一存在：  
  
-   不采用任何参数并返回一个对象的状态信息。  
  
-   接受一个参数设置对象的状态的某些部分。  
  
 属性的行为就如同它们是字段;如果方法不能则它应不会更改的属性。 方法是在以下情况下属性更好：  
  
-   方法执行耗时的操作。 该方法速度明显较慢比所需设置或获取的字段值的时间。  
  
-   该方法执行转换。 访问字段不返回它存储的数据的转换后的版本。  
  
-   Get 方法具有明显的副作用。 检索字段的值才会产生任何副作用。  
  
-   执行的顺序很重要。 设置字段的值不依赖于其他操作的匹配项。  
  
-   连续两次调用该方法创建不同的结果。  
  
-   该方法是静态的但返回的对象，可以更改由调用方。 检索字段的值不允许调用方，若要更改的字段中存储的数据。  
  
-   该方法返回一个数组。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，更改到属性的方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果方法不能满足上文所列条件中至少一个，禁止显示此规则的警告。  
  
## <a name="controlling-property-expansion-in-the-debugger"></a>控制在调试器中的属性扩展  
 程序员避免使用属性的一个原因是因为它们不希望调试器自动展开。 例如，属性可能会涉及分配一个大型对象或调用使用 P/Invoke，但它实际上可能不具有任何明显的副作用。  
  
 你可以防止调试器自动扩展通过应用属性<xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>。 下面的示例演示此特性应用到一个实例属性。  
  
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
  
```csharp  
  
      using System;   
using System.Diagnostics;   
  
namespace Microsoft.Samples   
{   
    publicclass TestClass   
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
  
## <a name="example"></a>示例  
 下面的示例包含几种方法，应将转换为属性，并且多个，应该不是因为它们不类似于字段。  
  
 [!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]