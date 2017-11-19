---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-method
title: "提取方法重构 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e85e745241d8fa880098b73a6306cbca3f19da70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extract-method-refactoring-c"></a>提取方法重构 (C#)
**提取方法**是重构操作，可以轻松地从现有成员中的代码段创建一个新方法。  
  
 使用**提取方法**，你可以通过提取中的现有成员的代码块中的代码的一组创建一个新方法。 新，提取方法包含所选的代码，并在现有成员中的所选的代码替换为新方法的调用。 将代码片段转变为其自己的方法使你能够快速地和准确地重新组织更好地重用和可读性代码。  
  
 **提取方法**具有以下优点：  
  
-   通过强调离散、 可重复使用的方法会促使最佳编码做法。  
  
-   鼓励自行记录通过较好的组织的代码。  
  
     描述性名称时使用的高级方法可以像读取一系列的注释。  
  
-   鼓励细粒度方法来简化重写创建。  
  
-   可以减少代码重复。  
  
### <a name="to-use-extract-method"></a>若要使用提取方法  
  
1.  创建名为 `ExtractMethod` 的控制台应用程序，然后将 `Program` 替换为下面的示例代码。  
  
    ```csharp  
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
  
2.  选择你想要提取的代码片段：  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  上**重构**菜单上，单击**提取方法**。  
  
     **提取方法**对话框随即出现。  
  
     或者，你还可以键入键盘快捷键 CTRL + R、 M 键显示**提取方法**对话框。  
  
     你还可以右键单击所选代码中，依次指向**重构**，然后单击**提取方法**以显示**提取方法**对话框。  
  
4.  指定的名称的新方法，如`CircleArea`中**新方法名称**框。  
  
     新的方法签名的预览显示在下**预览方法签名**。  
  
5.  单击“确定”。  
  
## <a name="remarks"></a>备注  
 当你使用**提取方法**命令时，同一类中的源成员之后插入新方法。  
  
## <a name="partial-types"></a>分部类型  
 如果此类是分部类型，然后**提取方法**生成紧跟源成员的新方法。 **提取方法**确定新方法，通过新的方法中的代码不引用任何实例数据时创建的静态方法的签名。  
  
## <a name="generic-type-parameters"></a>泛型类型参数  
 当您提取具有不受约束的泛型类型参数的方法时，生成的代码将不添加`ref`修饰符添加到该参数构造除非向其分配的值。 如果提取的方法将支持引用类型作为泛型类型参数，则你应该手动添加`ref`到方法签名中的参数修饰符。  
  
## <a name="anonymous-methods"></a>匿名方法  
 如果你尝试提取匿名方法，它包含指向声明或引用外部匿名方法的本地变量引用的一部分，则 Visual Studio 将警告你潜在语义的更改。  
  
 当匿名方法使用本地变量的值时，那一刻执行匿名方法被获取的值。 当匿名方法提取到另一种方法时，对提取的方法的调用时刻获取本地变量的值。  
  
 下面的示例演示此语义的更改。 如果执行此代码，然后**11**将打印到控制台。 如果你使用**提取方法**要提取的代码注释标记到其自己的方法的代码区域，然后再执行了重构的代码， **10**将打印到控制台。  
  
```csharp  
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
  
 若要解决这种情况下，请在类的匿名方法字段中使用的本地变量。  
  
## <a name="see-also"></a>另请参阅  
 [重构 (C#)](refactoring-csharp.md)