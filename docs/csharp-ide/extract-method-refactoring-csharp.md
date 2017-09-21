---
title: "提取方法重构 (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.extractmethod"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "重构 [C#]，提取方法"
  - "提取方法重构操作 [C#]"
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 提取方法重构 (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**“提取方法”**是一项重构操作，提供了一种从现有成员中的代码段创建新方法的便捷方式。  
  
 使用**“提取方法”**，可以通过从现有成员的代码块中提取一组代码来创建新方法。  提取出的新方法包含所选代码，而现有成员中的所选代码被替换为对新方法的调用。  通过将代码段变为其自己的方法，可以快速而准确地重新组织代码，以获得更好的重用性和可靠性。  
  
 **“提取方法”**有以下优点：  
  
-   通过强调离散的可重用方法鼓励最佳的编码做法。  
  
-   鼓励通过较好的组织获得自记录代码。  
  
     当使用描述性名称时，高级别方法可以像读取一系列注释一样进行读取。  
  
-   鼓励创建细化方法，以简化重载。  
  
-   减少代码重复。  
  
### 使用“提取方法”  
  
1.  创建名为 `ExtractMethod` 的控制台应用程序，然后使用以下代码示例替换 `Program`。  
  
    ```c#  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2.  选择您要提取的代码片段：  
  
    ```c#  
    double area = PI * radius * radius;  
  
    ```  
  
3.  在**“重构”**菜单上，单击**“提取方法”**。  
  
     出现**“提取方法”**对话框。  
  
     也可以键入键盘快捷键 Ctrl\+R、Ctrl\+M 来显示**“提取方法”**对话框。  
  
     还可以右击选定代码，指向**“重构”**，然后单击**“提取方法”**来显示**“提取方法”**对话框。  
  
4.  在**“新方法名称”**框中指定新方法的名称，如 `CircleArea`。  
  
     新方法签名的预览显示在**“预览方法签名”**下。  
  
5.  单击**“确定”**。  
  
## 备注  
 使用**“提取方法”**命令时，将在同一个类中的源成员之后插入新方法。  
  
## 分部类型  
 如果类是分部类型，则**“提取方法”**将紧跟源成员之后生成新方法。  **“提取方法”**确定新方法的签名，并在新方法中的代码不引用实例数据时创建静态方法。  
  
## 泛型类型参数  
 当您提取的方法具有不受约束的泛型类型参数时，除非已为该参数赋值，否则生成的代码将不向该参数添加 `ref` 修饰符。  如果提取的方法将支持引用类型作为泛型类型实参，则应该向方法签名中的形参手动添加 `ref` 修饰符。  
  
## 匿名方法  
 如果您尝试提取匿名方法（该方法包括对在匿名方法之外声明或引用的局部变量的引用）的一部分，则 Visual Studio 将警告您可能有语义更改。  
  
 当匿名方法使用局部变量的值时，将在执行匿名方法时获取该值。  将匿名方法提取到其他方法中时，将在调用提取方法时获取局部变量的值。  
  
 下面的示例阐释这一语义更改。  如果执行此代码，则将向控制台输出 **11**。  如果使用**“提取方法”**将代码注释所标记的代码区域提取到其自己的方法中，然后执行重构后的代码，则将向控制台输出 **10**。  
  
```c#  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 若要解决此问题，请使匿名方法中使用的局部变量成为类的字段。  
  
## 请参阅  
 [重构 \(C\#\)](../csharp-ide/refactoring-csharp.md)