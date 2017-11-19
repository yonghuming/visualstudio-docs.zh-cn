---
title: "CA1062： 验证公共方法的参数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f225159e551dac2327c35774db846eec4ccc6fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062：验证公共方法的自变量
|||  
|-|-|  
|TypeName|ValidateArgumentsOfPublicMethods|  
|CheckId|CA1062|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 外部可见方法取消其引用参数之一的引用而不验证该参数是否`null`(`Nothing`在 Visual Basic 中)。  
  
## <a name="rule-description"></a>规则说明  
 传递给外部可见方法的所有引用自变量应检查都是否为`null`。 适当时，引发<xref:System.ArgumentNullException>自变量时`null`。  
  
 如果可以从未知的程序集调用某个方法，因为它声明为公共或受保护，则应验证所有参数的方法。 如果该方法旨在只能由已知程序集调用，你应使该方法内部，并将应用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性设为包含该方法的程序集。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，验证每个引用参数是否为`null`。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果您确信函数中的另一个方法调用已验证的取消引用的参数，可以禁止显示此规则的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示与该规则冲突的方法以及满足该规则的方法。  
  
 ```csharp
 using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```
  
## <a name="example"></a>示例  
 在[!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)]，此规则不会检测正在传递给另一个执行验证的方法参数。  

```csharp
public string Method(string value)
{
    EnsureNotNull(value);

    // Fires incorrectly    
    return value.ToString();
}

private void EnsureNotNull(string value)
{
    if (value == null)
        throw new ArgumentNullException("value");
}
```

```vb
Public Function Method(ByVal value As String) As String
    EnsureNotNull(value)

    ' Fires incorrectly    
    Return value.ToString()
End Function

Private Sub EnsureNotNull(ByVal value As String)
    If value Is Nothing Then
        Throw (New ArgumentNullException("value"))
    End If
End Sub
```

## <a name="example"></a>示例  
 填充字段或属性时引用对象的复制构造函数也可能违反 CA1062 规则。 因为复制到复制构造函数传递的对象可能会发生了冲突`null`(`Nothing`在 Visual Basic 中)。 若要解决冲突，请使用静态 （在 Visual Basic 中的为共享） 方法来检查复制的对象不为 null。  
  
 在下面的示例`Person`类示例`other`对象传递给`Person`复制构造函数可能`null`。  
  
```csharp  
public class Person  
{  
    public string Name { get; private set; }  
    public int Age { get; private set; }  
  
    public Person(string name, int age)  
    {  
        Name = name;  
        Age = age;  
    }  
  
    // Copy constructor CA1062 fires because other is dereferenced  
    // without being checked for null  
    public Person(Person other)  
        : this(other.Name, other.Age)  
    {  
    }  
}  
```
  
## <a name="example"></a>示例  
 在以下修订`Person`示例中，`other`传递给复制构造函数的对象将首先检查是否存在 null 中`PassThroughNonNull`方法。  
  
```csharp  
public class Person  
{  
    public string Name { get; private set; }  
    public int Age { get; private set; }  
  
    public Person(string name, int age)  
    {  
        Name = name;  
        Age = age;  
    }  
  
    // Copy constructor  
    public Person(Person other)  
        : this(PassThroughNonNull(other).Name,   
          PassThroughNonNull(other).Age)  
    {   
    }  
  
    // Null check method  
    private static Person PassThroughNonNull(Person person)  
    {  
        if (person == null)  
            throw new ArgumentNullException("person");  
        return person;  
    }  
}  
  
```