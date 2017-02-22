---
title: "How to: Split a Class into Partial Classes (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer, partial classes"
  - "partial classes, Class Designer"
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Split a Class into Partial Classes (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过在 Visual Basic 中使用 `Partial` 关键字或在 Visual C\# 中使用 `partial` 关键字，可以将类或结构的声明拆分到多个声明中。  可以根据需要在任意多个不同的源文件中或在一个源文件中使用任意数量的分部声明。  但所有声明必须位于同一程序集和命名空间中。  
  
 分部类在多种情况下是十分有用的。  例如，在处理大型项目时，通过将某个类拆分为多个文件，使多个程序员可以同时处理该类。  如果使用的是 Visual Studio 所生成的代码，则无需重新创建源文件就可更改该类。  （Visual Studio 生成的代码的示例包括 Windows 窗体和 Web 服务包装代码。）因此，无需修改 Visual Studio 创建的文件，就可创建使用自动生成的类的代码。  
  
 有两种分部方法。  在 Visual C\# 中，它们称为声明 \(Declaring\) 和实现 \(Implementing\)；在 Visual Basic 中，它们称为声明 \(Declaration\) 和实现 \(Implementation\)。  
  
 类设计器支持分部类和分部方法。  类关系图中的类型形状引用分部类的单个声明位置。  如果在多个文件中定义了分部类，则可以通过设置**“属性”**窗口中的**“新成员位置”**属性来指定类设计器将使用的声明位置。  也就是说，当您双击某个类形状时，类设计器就会转至包含**“新成员位置”**属性所标识的类声明的源文件。  双击类形状中的某个分部方法时，类设计器会转至分部方法声明。  此外，**“属性”**窗口中的**“文件名”**属性也引用声明位置。  对于分部类，**“文件名”**列出了包含该类的声明和实现代码的所有文件。  但对于分部方法，**“文件名”**仅列出了包含分部方法声明的文件。  
  
 下面的示例将类 `Employee` 的定义拆分为两个声明，其中每个声明分别定义一个不同的过程。  这些示例中的两个分部定义既可位于一个源文件中，也可位于两个不同的源文件中。  
  
> [!NOTE]
>  Visual Basic 使用分部类定义将 Visual Studio 生成的代码与用户创作的代码分隔开。  这些代码被分隔成离散的源文件。  例如，**“Windows 窗体设计器”**为控件定义的分部类，如 `Form`。  不应修改在这些控件中生成的代码。  
  
 有关 Visual Basic 中的分部类型的更多信息，请参见 [分部](/dotnet/visual-basic/language-reference/modifiers/partial)。  
  
## 示例  
 若要在 Visual Basic 中拆分类定义，请使用 `Partial` 关键字，如下面的示例所示。  
  
```vb#  
' First part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateWorkHours()  
    End Sub  
End Class  
  
' Second part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateTaxes()  
    End Sub  
End Class  
```  
  
## 示例  
 若要在 Visual C\# 中拆分类定义，请使用 `partial` 关键字，如下面的示例所示。  
  
```c#  
// First part of class definition.  
public partial class Employee  
{  
    public void CalculateWorkHours()  
    {  
    }  
}  
  
// Second part of class definition.  
public partial class Employee  
{  
    public void CalculateTaxes()  
    {  
    }  
}  
```  
  
## 请参阅  
 [分部类和方法](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [分部（类型）](/dotnet/csharp/language-reference/keywords/partial-type)   
 [分部（方法）（C\# 参考）](/dotnet/csharp/language-reference/keywords/partial-method)   
 [分部](/dotnet/visual-basic/language-reference/modifiers/partial)