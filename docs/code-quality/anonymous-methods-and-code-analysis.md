---
title: "匿名方法和代码分析 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "匿名方法, 代码分析"
  - "代码分析, 匿名方法"
  - "方法, 匿名"
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 匿名方法和代码分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“匿名方法”就是没有名称的方法。  匿名方法通常用于将代码块作为委托参数进行传递。  
  
 本主题介绍代码分析如何处理与匿名方法关联的警告和度量。  
  
## 成员中声明的匿名方法  
 在某个成员（如方法或访问器）中声明的匿名方法的警告和度量与声明该方法的成员相关联，  而不与调用该方法的成员关联。  
  
 例如，在下面的类中，**anonymousMethod** 的声明中出现的任何警告，都应针对 **Method1** 而不是 **Method2** 引发。  
  
```vb#  
  
        Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As  Integer) value > 5  
        Method2(anonymousMethod)  
    End Sub Sub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End Sub End Class  
```  
  
```c#  
  
        delegate void Delegate();  
class Class  
{  
    void Method1()  
    {  
        Delegate anonymousMethod = delegate()   
        {   
          Console.WriteLine("");   
        }  
        Method2(anonymousMethod);  
    }  
  
    void Method2(Delegate anonymousMethod)  
    {  
        anonymousMethod();  
    }  
}  
```  
  
## 内联匿名方法  
 声明为向字段内联赋值的匿名方法的警告和度量与构造函数相关联。  如果字段声明为 `static`（[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 `Shared`），则警告和度量与类构造函数相关联；否则，与实例构造函数相关联。  
  
 例如，在下面的类中，**anonymousMethod1** 的声明中出现的任何警告，都将针对隐式生成的默认 **Class** 构造函数引发。  而 **anonymousMethod2** 中出现的警告，则将针对隐式生成的类构造函数应用。  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As     Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As      Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End Sub End Class  
```  
  
```c#  
  
        delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod1 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    static Delegate anonymousMethod2 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    void Method()  
    {  
       anonymousMethod1();  
       anonymousMethod2();  
    }  
}  
```  
  
 类可以包含一个内联匿名方法，用以向具有多个构造函数的字段赋值。  这种情况下，警告和度量与所有构造函数相关联，除非构造函数链接到同一个类的另一个构造函数。  
  
 例如，在下面的类中，**anonymousMethod** 的声明中出现的任何警告，都应针对 **Class\(int\)** 和 **Class\(string\)** 而不是 **Class\(\)** 引发。  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
Sub New()  
    New(CStr(Nothing))  
End Sub Sub New(ByVal a As Integer)  
End Sub Sub New(ByVal a As String)  
End Sub End Class  
```  
  
```c#  
  
        delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    Class() : this((string)null)  
    {  
    }  
  
    Class(int a)  
    {  
    }  
  
    Class(string a)  
    {  
    }  
}  
```  
  
 即使这看起来有点意外，但由于编译器会为未链接到其他构造函数的每个构造函数都输出一个唯一的方法，因此就会出现这种情况。  由于存在这一行为，在 **anonymousMethod** 内出现的任何冲突都必须单独禁止显示。  这也意味着，如果引入新的构造函数，以前针对 **Class\(int\)** 和 **Class\(string\)** 禁止显示的警告也必须针对新构造函数禁止显示。  
  
 这个问题可通过下面两种方法解决。  一是在所有构造函数都与之链接的公共构造函数中声明 **anonymousMethod**。  二是在所有构造函数都调用的初始化方法中声明该方法。  
  
## 请参阅  
 [分析托管代码质量](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)