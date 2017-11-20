---
redirect_url: /visualstudio/csharp-ide/refactoring/rename
title: "重命名重构 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eba5a9f55e5d3d08eee48dc083a7e2f848118162
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="rename-refactoring-c"></a>重命名重构 (C#)
**重命名**是可以轻松地重命名标识符代码符号，如字段、 局部变量、 方法、 命名空间、 属性和类型的 Visual Studio 集成的开发环境 (IDE) 中的重构功能。 **重命名**可用来更改名称和字符串中的注释，并且若要更改的声明和调用的标识符。  
  
> [!NOTE]
>  当 for Visual Studio 使用源代码管理，获取源的最新版本之前尝试执行重命名重构。  
  
 重命名重构可从以下 Visual Studio 功能：  
  
|功能|在 IDE 中重构的行为|  
|-------------|----------------------------------------|  
|代码编辑器|当您将光标定位在某些类型的代码符号上，在代码编辑器中，重命名重构功能才可用。 当光标位于此位置时，你可以调用**重命名**命令通过键入 （Ctrl + R、 Ctrl + R） 的键盘快捷方式或通过选择**重命名**命令从快速操作，快捷菜单中，或**重构**菜单。|  
|类视图|当在类视图中选择标识符时，重命名重构是可以从快捷菜单和**重构**菜单。|  
|对象浏览器|在对象浏览器中选择标识符，重命名重构功能后，才可从**重构**菜单。|  
|Windows 窗体设计器的属性网格|在**属性网格**的 Windows 窗体设计器中，更改控件的名称将启动重命名操作该控件。 **重命名**对话框中将不会出现。|  
|“解决方案资源管理器”|在**解决方案资源管理器**、**重命名**命令是快捷菜单上提供。 如果所选的源文件包含其类名为的文件名称相同的类，可以使用此命令可以同时重命名的源文件和执行重命名重构。<br /><br /> 例如，如果创建一个默认的基于 Windows 的应用程序，然后将 Form1.cs 重命名为 TestForm.cs 源文件名 Form1.cs 将改为 TestForm.cs 和类 form1，所有引用，类将重命名为 TestForm。 **注意：** **撤消**命令 (CTRL + Z) 将只撤消重命名重构代码中，并将不更改的文件名称回原始名称。 <br /><br /> 如果所选的源文件不包含一个类，其名称是相同的文件名称，**重命名**命令**解决方案资源管理器**将仅重命名源文件而不会执行重命名重构。|  
  
## <a name="rename-operations"></a>重命名操作  
 执行时**重命名**下, 表中所述，重构引擎将执行特定于每个代码符号，重命名操作。  
  
|代码符号|重命名操作|  
|-----------------|----------------------|  
|字段|声明和用法的字段更改为新的名称。|  
|本地变量|声明和用法的变量更改为新的名称。|  
|方法|为新的名称更改的方法和到该方法的所有引用的名称。 **注意：**时重命名的扩展方法，重命名操作将传播到方法的作用域，而不考虑是否使用静态方法或实例方法作为扩展方法中的所有实例。 有关详细信息，请参阅[扩展方法](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)|  
|命名空间|命名空间的名称将更改为新名称在声明中，所有`using`语句和完全限定的名称。 **注意：**时重命名命名空间中，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]还会更新**默认 Namespace**属性**应用程序**页**项目设计器**. 此属性不能通过选择重置**撤消**从**编辑**菜单。 若要重置**默认 Namespace**属性值，则必须修改中的属性**项目设计器**。 有关详细信息，请参阅[应用程序页](../ide/reference/application-page-project-designer-csharp.md)。|  
|属性|声明和用法的属性更改为新的名称。|  
|类型|所有声明和使用的类型的所有实例更改为新名称，包括构造函数和析构函数。 为分部类型重命名操作将会传播到所有部分。|  
  
#### <a name="to-rename-an-identifier"></a>若要重命名标识符  
  
1.  创建名为 `RenameIdentifier` 的控制台应用程序，然后将 `Program` 替换为下面的示例代码。  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  将光标放在`MethodB`，在方法声明或方法调用。  
  
3.  从**重构**菜单上，选择**重命名**。 **重命名**对话框随即出现。  
  
     此外可以右键单击将光标置于，指向**重构**上下文菜单，然后单击**重命名**以显示**重命名**对话框。  
  
4.  在**新名称**字段中，键入`MethodC`。  
  
5.  选择**在注释中的搜索**复选框。  
  
6.  单击“确定”。  
  
7.  在**预览更改**对话框中，单击**应用**。  
  
#### <a name="to-rename-an-identifier-using-quick-actions"></a>若要重命名标识符使用快速操作  
  
1.  创建名为 `RenameIdentifier` 的控制台应用程序，然后将 `Program` 替换为下面的示例代码。  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  声明中`MethodB`，键入或按 backspace 方法标识符。 快速操作电灯泡会在边距中显示。  
  
    > [!NOTE]
    >  你仅可以调用在标识符的声明中使用快速操作重命名重构。  
  
3.  键入的键盘快捷方式**Shift + Alt + F10**以显示快速操作菜单。  
  
     - 或 -  
  
     单击旁边灯泡以显示快速操作菜单上的黑色三角形。  
  
4.  选择**重命名\<identifer1 > 到\<identifier2 >**菜单项，以调用重命名重构。 对所有引用 **\<identifer1 >**将自动更新到 **\<identifier2 >**。  
  
## <a name="remarks"></a>备注  
  
## <a name="renaming-implemented-or-overridden-members"></a>重命名实现或重写的成员  
 当你**重命名**实现/重写或是实现/的成员重写中其他类型的成员[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]显示一个对话框，说明该重命名操作将导致级联更新。 如果你单击**继续**、 重构引擎以递归方式查找，并将重命名基中的所有成员和具有的派生的类型实现/重写关系与要重命名的成员。  
  
 下面的代码示例包含具有实现/重写关系的成员。  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../csharp-ide/codesnippet/CSharp/rename-refactoring-csharp_1.cs)]  
  
 在前面的示例中，重命名`C.Method()`也将重命名`Ibase.Method()`因为`C.Method()`实现`Ibase.Method()`。 接下来，则重构引擎将递归发现`Ibase.Method()`由实现`Derived.Method()`并将重命名`Derived.Method()`。 重构引擎不是重命名`Base.Method()`，这是因为`Derived.Method()`不重写`Base.Method()`。 重构引擎将在此处停止除非你有**重命名重载**签入**重命名**对话框。  
  
 如果**重命名重载**已选中，将重命名重构引擎`Derived.Method(int i)`因为它重载`Derived.Method()`，`Base.Method(int i)`因为它被覆盖`Derived.Method(int i)`，和`Base.Method()`的重载，因为它`Base.Method(int i)`.  
  
> [!NOTE]
>  重命名中引用的程序集中定义的成员时，对话框中的文字重命名会导致生成错误。  
  
## <a name="renaming-properties-of-anonymous-types"></a>重命名的匿名类型的属性  
 重命名中匿名类型的属性时，重命名操作将传播到其他具有相同的属性的匿名类型中的属性。 下面的示例说明了此行为。  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 在前面的代码中，重命名`ID`将更改`ID`两个语句中因为它们具有相同的基础匿名类型。  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 在前面的代码中，重命名`ID`将仅重命名的一个实例`ID`因为`companyIDs`和`orderIDs`不具有相同的属性。  
  
## <a name="see-also"></a>另请参阅  
 [重构 (C#)](refactoring-csharp.md)   
 [匿名类型](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)