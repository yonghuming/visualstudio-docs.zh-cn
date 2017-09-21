---
title: "CA1062：验证公共方法的参数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
  - "Validate arguments of public methods"
helpviewer_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1062：验证公共方法的参数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ValidateArgumentsOfPublicMethods|  
|CheckId|CA1062|  
|类别|Microsoft.Design|  
|是否重大更改|否|  
  
## 原因  
 外部可见的方法取消对它的某个引用参数的引用，而没有验证该参数是否为 `null`（在 Visual Basic 中为 `Nothing`）。  
  
## 规则说明  
 对于传递给外部可见方法的所有引用参数，都应检查其是否为 `null`。  适当的情况下，当参数为 `null` 时将引发 <xref:System.ArgumentNullException>。  
  
 如果某个方法由于声明为公共类型或受保护类型而可以从未知的程序集调用，则应验证该方法的所有参数。  如果方法被设计为仅由已知程序集调用，则应使该方法成为内部样式，并将 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 特性应用于包含该方法的程序集。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请验证每个引用参数是否为 `null`。  
  
## 何时禁止显示警告  
 如果您确信取消引用的参数已借助函数中的另一方法调用通过验证，可以从该规则禁止警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的方法和一个满足该规则的方法。  
  
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_1.vb)]  
  
## 示例  
 在 [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] 中，此规则不会检测要传递给执行验证的其他方法的参数。  
  
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_2.vb)]  
  
## 示例  
 填充字段的复制构造函数或引用对象的属性也可能违反 CA1062 规则。  因为传递给复制构造函数的复制的对象可能为 `null`（`Nothing`，Visual Basic 中），因此会发生冲突。  若要解决该冲突，使用静态的（在 Visual Basic 中的共享）方法检查复制的对象是否非 null。  
  
 在下面的 `Person` 类示例中，传递给 `Person` 复制构造函数的 `other` 对象可能是 `null`。  
  
```  
  
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
  
## 示例  
 在下面的修改后的 `Person` 示例中，传递给复制构造函数的 `other` 对象首先在 `PassThroughNonNull` 方法中检查其是否为 null。  
  
```  
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