---
title: "匿名方法和代码分析 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8ebf550ca92cbefbed684e2b11e0b20b62661133
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="anonymous-methods-and-code-analysis"></a>匿名方法和代码分析
*匿名方法*是没有名称的方法。 匿名方法是最常用于将代码块作为委托参数传递。  
  
 本主题说明代码分析警告和与匿名方法相关联的度量值的处理。  
  
## <a name="anonymous-methods-declared-in-a-member"></a>在成员中声明的匿名方法  
 警告和匿名方法中的成员，如方法或访问器，声明的度量值都与声明方法的成员关联。 它们不具有成员的调用的方法相关联。  
  
 例如，在下面的类的声明中找到任何警告**anonymousMethod**应针对引发**Method1**和 not **Method2**。  
  
```vb  
  
      Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5  
        Method2(anonymousMethod)  
    End SubSub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End SubEnd Class  
```  
  
```csharp  
  
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
  
## <a name="inline-anonymous-methods"></a>内联匿名方法  
 警告和度量值被声明为内联赋值给的字段的匿名方法是使用构造函数相关联。 如果字段声明为`static`(`Shared`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])、 警告和度量值是与类构造函数; 否则为它们是实例构造函数与相关联。  
  
 例如，在下面的类的声明中找到任何警告**anonymousMethod1**将针对的隐式生成的默认构造函数引发**类**。 而这些位于**anonymousMethod2**将应用针对隐式生成的类构造函数。  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End SubEnd Class  
```  
  
```csharp  
  
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
  
 类可以包含内联匿名方法，将值分配给具有多个构造函数的字段。 在这种情况下，警告和度量值都与关联的所有构造函数除非该构造函数将链接到同一类中的另一个构造函数。  
  
 例如，在下面的类的声明中找到任何警告**anonymousMethod**应针对引发**Class(int)**和**Class(string)**但不是针对**Class()**。  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
SubNew()  
    New(CStr(Nothing))  
End SubSub New(ByVal a As Integer)  
End SubSub New(ByVal a As String)  
End SubEnd Class  
```  
  
```csharp  
  
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
  
 尽管这看起来有点意外，这是因为编译器输出为每个构造函数都未链接到另一个构造函数的唯一方法。 由于此行为，任何违反它将出现在**anonymousMethod**必须单独取消。 这也意味着，如果新的构造函数是引入了针对以前禁止显示警告**Class(int)**和**Class(string)**必须也被抑制针对新的构造函数。  
  
 你可以解决此问题的两种方式之一。 你可以声明**anonymousMethod**公共构造函数中的所有构造函数链。 或者，你无法将其声明中初始化方法调用的所有构造函数。  
  
## <a name="see-also"></a>另请参阅  
 [分析托管代码质量](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)