---
title: "如何：将类拆分为分部类（类设计器）| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: a92d03bca26e1e3eceacb3b611d81e344b656393
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>如何：将类拆分为分部类（类设计器）
可以通过使用 Visual Basic 中的 `Partial` 关键字或 Visual C# 中的 `partial` 关键字来划分类声明或多个声明中的结构。 可以根据需要在任意数量的不同源文件中或一个源文件中使用任意数量的分部声明。 但是，所有声明都必须在相同的程序集和相同的命名空间中。  
  
 分部类在以下几种情况下有用。 例如，在使用大型项目时，将类分隔到多个文件可以使多个程序员同时对其进行处理。 在使用 Visual Studio 生成的代码时，可以更改类，而无需重新创建源文件。 （Visual Studio 生成的代码的示例包括 Windows 窗体和 Web 服务包装器代码。）因此，无需修改 Visual Studio 创建的文件，就可以创建使用自动生成的类的代码。  
  
 有两种分部方法。 在 Visual C# 中，它们被称为 declaring 和 implementing；而在 Visual Basic 中，它们被称为 declaration 和 implementation。  
  
 类设计器支持分部类和方法。 类图中的类型形状是指分部类的单个声明位置。 如果分部类在多个文件中定义，则可以通过在“属性”窗口中设置“New Member Location”属性来指定将要使用的声明位置类设计器。 也就是说，双击类形状时，类设计器就会转到包含由“New Member Location”属性标识的类声明的源文件。 双击类形状中的分部方法时，类设计器会转到分部方法声明。 此外，在“属性”窗口中，“File Name”属性是指声明位置。 对于分部类，“File Name”列出包含该类的声明和实现代码的所有文件。 但是，对于分部方法，“File Name”仅列出包含分部方法声明的文件。  
  
 下面的示例将类 `Employee` 的定义拆分到两个声明中，其中每一个均定义一个不同的过程。 示例中的两个分部定义可能在一个源文件中或在两个不同的源文件中。  
  
> [!NOTE]
>  Visual Basic 使用分部类定义将 Visual Studio 生成的代码与用户编写的代码分开。 代码被分成单独的源文件。 例如，“Windows 窗体设计器”定义了控件的分部类，如 `Form`。 不应修改这些控件中生成的代码。  
  
 有关 Visual Basic 中分部类型的详细信息，请参阅[分部](/dotnet/visual-basic/language-reference/modifiers/partial)。  
  
## <a name="example"></a>示例  
 若要拆分 Visual Basic 中的类定义，请使用 `Partial` 关键字，如以下示例所示。  
  
```vb  
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
  
## <a name="example"></a>示例  
 若要拆分 Visual C# 中的类定义，请使用 `partial` 关键字，如以下示例所示。  
  
```csharp  
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
  
## <a name="see-also"></a>另请参阅  
 [分部类和方法](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [分部（类型）](/dotnet/csharp/language-reference/keywords/partial-type)   
 [分部（方法）（C# 参考）](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)
