---
title: "快速操作 | Microsoft Docs"
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: e173fb7d-c5bd-4568-ba0f-aa61913b3244
author: kempb
ms.author: kempb
manager: ghogen
dev_langs:
- CSharp
- VB
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: ec2ae70312c7cb5f26630246046cadc7c210e1c2
ms.contentlocale: zh-cn
ms.lasthandoff: 05/26/2017

---
# 快速操作
<a id="quick-actions" class="xliff"></a>

通过[快速操作](refactoring-code-generation-quick-actions.md#quick-actions)，只凭单个操作便可轻松重构、生成或修改代码。  尽管许多快速操作仅专门适用于 C# 或 Visual Basic，但也有一些快速操作同时适用于 C# 和 Visual Basic 项目。  可使用灯泡图标![小灯泡图标](~/ide/media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall")，或按“Ctrl+.”应用这些快速操作， 前提是光标位于相应的代码行上。

如果有红色波形曲线，则将看到灯泡，Visual Studio 针对如何解决此问题有一条建议。 例如，如果你遇到红色波形曲线指示的错误，则在可对该错误进行修复时，会显示灯泡。 对于任何语言，第三方均可提供自定义诊断和建议（例如，作为 SDK 的一部分），Visual Studio 电灯泡会根据这些规则亮起。  

### 查看电灯泡
<a id="to-see-a-light-bulb" class="xliff"></a>  

1. 在许多情况下，灯泡会在你将鼠标指针悬停在错误点上方时，或是在你将插入点移动到存在错误的行中时在编辑器左边距处自然而然地出现。 看到红色波形曲线时，可悬停在其上方，以显示电灯泡。 使用鼠标或键盘转到问题发生的行时，也会显示电灯泡。  

2. 在行上的任意位置按“Ctrl + .” 可调用电灯泡并直接转到潜在修复列表。  

   ![带鼠标悬停的灯泡](~/ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")  

### 查看潜在修复
<a id="to-see-potential-fixes" class="xliff"></a>  
单击向下箭头或“显示潜在修复”链接，以显示电灯泡可执行的快速操作列表。  

![灯泡已展开](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## 常见快速操作
<a id="common-quick-actions" class="xliff"></a>
下面是同时适用于 C# 和 Visual Basic 代码的一些常见快速操作。

### 添加缺少的 case/默认 case/二者
<a id="add-missing-casesdefault-caseboth" class="xliff"></a>
在 C# 中创建 `switch` 语句，或在 Visual Basic 中创建 `Select Case` 语句时，可使用代码操作自动添加缺少的 case 项、默认 case 语句或同时添加二者。  对于如下所示的空语句：

```CSharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```VB
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

使用“添加两者”快速操作同时填入缺少 的 case 和默认 case 将创建以下内容：

```CSharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```VB
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

### 更正拼写错误的类型
<a id="correct-misspelled-type" class="xliff"></a>
如果在 Visual Studio 中意外拼错了一个类型，此快速操作会为你自动更正错误。  可在灯泡菜单中看到这些项显示有“‘将拼写错误的类型’更改为‘正确类型’”。  例如：

```CSharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```VB
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

### 删除不必要的 cast
<a id="remove-unnecessary-cast" class="xliff"></a>
如果将某类型强制转换为不需要 cast 的另一类型，则“删除不必要的 cast”快速操作将从代码中删除该 cast。

```CSharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```VB
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

### 将方法替换为属性/将属性替换为方法
<a id="replace-method-with-property--replace-property-with-method" class="xliff"></a>
这些快速操作可将方法转换为属性，反之亦然。  以下示例演示了从方法到属性的转换。  相反情况下，只需将 *Before* 和 *After* 部分颠倒过来即可。

```CSharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

```VB
Dim MyValue As Integer

' Before
Function GetMyValue() As Integer
    Return MyValue
End Function

' Replace 'GetMyValue' with property

' After
ReadOnly Property MyValue As Integer
    Get
        Return MyValue
    End Get
End Property
```

### 使方法同步
<a id="make-method-synchronous" class="xliff"></a>
在对方法使用 `async`/`Async` 关键字时，很有可能也会在该方法的内部某一位置使用 `await`/`Await` 关键字。  但是，如果不是这种情况，则会出现可通过删除 `async`/`Async` 关键字并更改返回类型以使方法同步的快速操作。  从“快速操作”菜单中使用“使方法同步”选项。

```CSharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```VB
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

### 使方法异步
<a id="make-method-asynchronous" class="xliff"></a>
在方法内使用 `await`/`Await` 关键字时，该方法本身很有可能会标记有 `async`/`Async` 关键字。  但是，如果不是这种情况，则会出现可使方法异步的快速操作。  从“快速操作”菜单中使用“使方法/函数异步”选项。

```CSharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method synchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```VB
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method synchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

### 删除不必要的 using/Import
<a id="remove-unnecesary-usingsimports" class="xliff"></a>
“删除不必要的 using/Import”快速操作将删除当前文件中任何未使用的 `using` 和 `Import` 语句。  选择此项后，将立即删除未使用的命名空间导入。

### 在引用程序集、NuGet 包或解决方案的其他类型中为类型添加 using/Import
<a id="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution" class="xliff"></a>
位于解决方案其他项目中的 using 类型将自动显示快速操作，但其他类型的快速操作则需要从“工具”>“选项”>“C#”或“基本”>“高级”选项卡中启用：  

* 建议对引用程序集中的类型使用 using/import
* 建议对 NuGet 包中的类型使用 using/import

启用后，如果使用当前未导入但引用程序集或 NuGet 包中存在的命名空间中的类型，则会创建 using/import 语句。

```CSharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```VB
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

### 转换为内插字符串
<a id="convert-to-interpolated-string" class="xliff"></a>
类似于 **[String.Format](https://msdn.microsoft.com/library/system.string.format.aspx)** 方法，[内插字符串](/dotnet/csharp/language-reference/keywords/interpolated-strings)是使用嵌入式变量来表达字符串的一种简单方式。  此快速操作可识别何时需要将字符串连接在一起或使用 **String.Format**，然后将用法更改为内插字符串。

```CSharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```VB
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

### 移除合并冲突标记
<a id="remove-merge-conflict-markers" class="xliff"></a>
借助这些快速操作，可以通过“接受更改”（即移除冲突的代码和标记）解决合并冲突问题。 （仅适用于 Visual Studio 2017（版本 15.3 - 预览版）。）

![重构 - 解决合并冲突](~/ide/media/vside-refactoring-merge-conflicts.png)

### 添加 null 参数检查
<a id="add-null-checks-for-parameters" class="xliff"></a>
借助此快速操作，可以在代码中添加检查，从而指明参数是否为 null。 （仅适用于 Visual Studio 2017（版本 15.3 - 预览版）。）

![重构 - 添加 null 检查](~/ide/media/vside-refactoring-nullcheck.png)

### 构造函数生成器改进
<a id="constructor-generator-improvements" class="xliff"></a>
借助此快速操作，可以在创建构造函数时选择要生成的属性或字段，也可以从空白主体生成构造函数。 此外，还可以从调用站点将参数添加到现有构造函数中。 （仅适用于 Visual Studio 2017（版本 15.3 - 预览版）。）

![重构 - 生成构造函数](~/ide/media/vside-refactoring-constructors.png)

### 删除未使用的变量
<a id="remove-unused-variables" class="xliff"></a>
借助此快速操作，可以从代码中删除已声明但从未用过的变量。 （仅适用于 Visual Studio 2017（版本 15.3 - 预览版）。）

![重构 - 未使用的变量](~/ide/media/vside-refactoring-unusedvars.png)

### 生成重写函数
<a id="generate-overrides" class="xliff"></a>
借助此快速操作，可以从类或结构中的空白行创建重写函数。 使用“选取成员”对话框，可以选择要重写的成员。 （仅适用于 Visual Studio 2017（版本 15.3 - 预览版）。）

![重构 - 重写函数](~/ide/media/vside-refactoring-overrides.png)

![重构 - 重写函数对话框](~/ide/media/vside-refactoring-overrides-dialog.png)

### 更改数字参数的基数
<a id="change-base-for-numeric-literals" class="xliff"></a>
借助此快速操作，可以将数字文本从一种基本数制转换成另一种。 例如，可以将数字更改为十六进制或二进制格式。 （仅适用于 Visual Studio 2017（版本 15.3 - 预览版）。）

![重构 - 更改基本数制](~/ide/media/vside-refactoring-changebase1.png)

![重构 - 更改基本数制](~/ide/media/vside-refactoring-changebase2.png)

### 将数字分隔符插入数字文本
<a id="insert-digit-separators-into-literals" class="xliff"></a>
借助此快速操作，可以将分隔符添加到数字文本值中。 （仅适用于 Visual Studio 2017（版本 15.3 - 预览版）。）

![重构 - 更改数字分隔符](~/ide/media/vside-refactoring-separators.png)

### 将 **if** 构造转换成 **switch**
<a id="convert-if-construct-to-switch" class="xliff"></a>
借助此快速操作，可以将 **if-then-else** 构造转换成 **switch** 构造。 （仅适用于 Visual Studio 2017（版本 15.3 - 预览版）。）

```CSharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);  
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```VB
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

# 另请参阅
<a id="see-also" class="xliff"></a>
* [代码样式和快速操作](code-styles-and-quick-actions.md)

