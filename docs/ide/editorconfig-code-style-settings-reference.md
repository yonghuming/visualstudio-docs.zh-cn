---
title: "EditorConfig 的 .NET 编码约定设置 | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 1
author: kaseyu
ms.author: kaseyu
manager: davidcsa
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
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: 71a0fadaefad47b16182f1166968207a26cc1d40
ms.contentlocale: zh-cn
ms.lasthandoff: 08/14/2017

---

# <a name="net-coding-convention-settings-for-editorconfig"></a>EditorConfig 的 .NET 编码约定设置
使用 [EditorConfig](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options) 文件配置 .NET 编码约定。 通过 EditorConfig 文件，可以启用/禁用单个 .NET 编码约定并配置强制实施约定的程度”（通过严重级别）。 若要了解有关如何使用 EditorConfig 强制实施代码库一致性的详细信息，请阅读[本文](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options)。

有三种受支持的 .NET 编码约定类别：
- **[语言约定](#language)**是与 C# 或 Visual Basic 语言相关的规则，例如 `var`/显式类型，使用 expression-bodied 成员。
- **[格式设置规则](#formatting)**是有关代码布局和结构的规则，以便使其更容易进行读取，例如控制块中使用的 Allman 大括号、空格。
- **[命名约定](#naming)**是遵从对象命名方式的规则，例如，`async` 方法必须以“Async”结尾。 

# <a name="language">语言约定</a>
## <a name="overview"></a>概述
**规则格式：**
`options_name = false|true : none|suggestion|warning|error`

对于代码样式选项，必须指定“true”（选择此选项）或“false”（不选择此选项）、冒号 (`:`) 及严重性（`none`、`silent`、`suggestion`、`warning` 或 `error`）。 严重性代表想在基本代码中应用的样式的强制级别。

`none` 和 `silent` 是同义词，表示不应向用户显示任何形式的指示。 下面介绍禁用此规则的效果。

严重性 | 效果
------------ | -------------
无/静默 | 如未遵循此样式，不会向用户显示任何内容，但会以该样式生成代码生成功能。 
建议 | 如未遵循此样式，以建议形式向用户显示此样式（前两个字符下带点）。
警告 | 如未遵循此样式，显示编译器警告。
错误 | 如未遵循此样式，显示编译器错误。

## <a name="net-language-convention-options"></a>.NET 语言约定选项

- **[.NET 代码样式设置](#this_and_me)**
    - [“This.”和“me.”限定](#this_and_me)
        - [字段](#this_and_me_fields)
        - [属性](#this_and_me_properties)
        - [方法](#this_and_me_methods)
        - [事件](#this_and_me_events)
    - [语言关键字（int 和 string 等）与类型引用的框架类型名称](#language_keywords)
        - [局部变量、参数和成员](#language_keywords_variables)
        - [成员访问表达式](#language_keywords_member_access)
    - [表达式级首选项](#expression_level)
        - [对象初始值设定项](#expression_level_object_initializers)
        - [集合初始值设定项](#expression_level_collection_initializers)
        - [显式元组名称](#expression_level_tuple_names)
        - [“null”检查中的合并表达式](#expression_level_null_checking)
        - [“null”检查中的 null 传播](#expression_level_null_propogation)
- **[CSharp 代码样式设置](#csharp_codestyle)**
    - [“var”](#var)
        - [内置类型的“var”](#var_built_in)
        - [类型为明显时的“var”](#var_apparent)
        - [其他位置的“var”](#var_elsewhere)
    - [Expression-Bodied 成员](#expression_body)
        - [方法](#expression_bodied_members_methods)
        - [构造函数](#expression_bodied_members_constructors)
        - [运算符](#expression_bodied_members_operators)
        - [属性](#expression_bodied_members_properties)
        - [索引器](#expression_bodied_members_indexers)
        - [访问器](#expression_bodied_members_accessors)
    - [模式匹配](#pattern_matching)
        - [“is”和“cast”检查](#pattern_matching_is_cast)
        - [“as”和“null”检查](#pattern_matching_as_null)
    - [内联变量声明](#inlined_variable_declarations)
    - [表达式级首选项](#expression_level_csharp) -[简化 `default` 表达式](#expression_level_default)
    - [“null”检查首选项](#null_checking)
        - [Throw 表达式](#null_checking_throw_expressions)
        - [条件委托调用](#null_checking_conditional_delegate_calls)
    - [代码块首选项](#code_block)
        - [首选大括号](#prefer_braces)

## <a name="this_and_me">“This.”和“me.”限定</a>
### <a name="this_and_me_fields">字段 (IDE0003/IDE0009)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `dotnet_style_qualification_for_field` | C# 和 Visual Basic | false:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 更喜欢非静态方法中使用的所有非静态字段以 `this.` 开始（在 C# 中）或以 `Me.` 开始（在 Visual Basic 中）。 | **C#：** <br>`this.capacity = 0;` <br><br> **Visual Basic：** <br> `Me.capacity = 0`
| False | 更喜欢非静态方法中使用的所有非静态字段不以 `this.` 开始（在 C# 中）或不以 `Me.` 开始（在 Visual Basic 中）。 | **C#：** <br>`capacity = 0;` <br><br> **Visual Basic：** <br>`capacity = 0`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">属性 (IDE0003/IDE0009)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_property`| C# 和 Visual Basic | false:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 更喜欢非静态方法中使用的所有非静态属性以 `this.` 开始（在 C# 中）或以 `Me.` 开始（在 Visual Basic 中）。| **C#：** <br>`this.ID = 0;` <br><br> **Visual Basic：** <br>`Me.ID = 0`
| False | 更喜欢非静态方法中使用的所有非静态属性不以 `this.` 开始（在 C# 中）或不以 `Me.` 开始（在 Visual Basic 中）。 | **C#：** <br>`ID = 0;` <br><br> **Visual Basic：** <br> `ID = 0`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```

### <a name="this_and_me_methods">方法 (IDE0003/IDE0009)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_method`| C# 和 Visual Basic | false:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 更喜欢从非静态方法中调用的所有非静态方法以 `this.` 开始（在 C# 中）和以 `Me.` 开始（在 VB 中）。| **C#：** <br>`this.Display();` <br><br> **Visual Basic：** <br> `Me.Display()`
| False | 更喜欢从非静态方法中调用的所有非静态方法不以 `this.` 开始（在 C# 中）和不以 `Me.` 开始（在 VB 中）。 | **C#：** <br>`Display();` <br><br> **Visual Basic：** <br> `Display()`


#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">事件 (IDE0003/IDE0009)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_event`| C# 和 Visual Basic | false:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 更喜欢从非静态方法中引用的所有非静态事件以 `this.` 开始（在 C# 中）和以 `Me.` 开始（在 VB 中）。| **C#：** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic：** <br> `AddHandler Me.Elapsed, AddressOf Handler`
| False | 更喜欢从非静态方法中引用的所有非静态事件不以 `this.` 开始（在 C# 中）和不以 `Me.` 开始（在 VB 中）。 | **C#：** <br>`Elapsed += Handler;` <br><br> **Visual Basic：** <br>`AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">语言关键字（int 和 string 等）与类型引用的框架类型名称</a>
### <a name="language_keywords_variables">局部变量、参数和成员 (IDE0012/IDE0014)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_predefined_type_for_locals_parameters_members`| C# 和 Visual Basic | true:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 对于局部变量、参数和类型成员，更喜欢具有语言关键字（用于表示它们）的类型（`int`、`double`、`float`、`short`、`long`、`decimal` 和 `string`），以使用关键字而不是类型名称（`Int32` 和 `Int64` 等）。| **C#：** <br>`private int _member;` <br><br> **Visual Basic：**`Private _member As Integer`
| False | 对于局部变量、参数和类型成员，更喜欢具有语言关键字（用于表示它们）的类型（`int`、`double`、`float`、`short`、`long`、`decimal` 和 `string`），以使用类型名称（`Int32` 和 `Int64` 等）而不是关键字。  | **C#：** <br>`private Int32 _member;` <br><br> **Visual Basic：** <br> `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">成员访问表达式 (IDE0013/IDE0015)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_predefined_type_for_member_access`| C# 和 Visual Basic | true:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 每当在具有关键字表示形式的类型上使用成员访问表达式时选择关键字（`int`、`double`、`float`、`short`、`long`、`decimal` 和 `string`）。| **C#：** <br>`var local = int.MaxValue;` <br><br> **Visual Basic：** <br> `Dim local = Integer.MaxValue`
| False | 每当在具有关键字表示形式的类型上使用成员访问表达式时选择类型名称（`int`、`double`、`float`、`short`、`long`、`decimal` 和 `string`）。 | **C#：** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic：** <br> `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">表达式级首选项</a>
### <a name="expression_level_object_initializers">对象初始值设定项 (IDE0017)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_object_initializer`| C# 和 Visual Basic | true:suggestion | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 在可能情况下，更倾向使用对象初始值设定项来初始化对象。| **C#：** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic：** <br> `Dim c = New Customer() With { .Age = 21 }`
| False | 更倾向不使用对象初始值设定项来初始化对象。 | **C#：** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic：** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">集合初始值设定项 (IDE0028)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_collection_initializer`| C# 和 Visual Basic | true:suggestion | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 在可能情况下，更倾向使用集合初始值设定项来初始化集合。| **C#：** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic：** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | 更倾向不使用集合初始值设定项来初始化对象。 | **C#：** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic：** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="expression_level_tuple_names">显式元组名称 (IDE0033)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_explicit_tuple_names`| C# 7.0+ 和 Visual Basic 15+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 比起 ItemX 属性更倾向元祖名称。| **C#：** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic：** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | 比起元组名称更倾向 ItemX 属性。 | **C#：** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic：** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="expression_level_null_checking">“null”检查中的合并表达式 (IDE0029)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_coalesce_expression`| C# 和 Visual Basic | true:suggestion | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 比起 三元运算符检查更倾向 null 合并表达式。| **C#：** <br>`var v = x ?? y;` <br><br> **Visual Basic：** <br> `Dim v = If(x, y)`
| False | 比起 null 合并表达式更倾向三元运算符检查。 | **C#：** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic：** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="expression_level_null_propogation">“null”检查中的 null 传播 (IDE0031)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_null_propagation`| C# 6.0+ 和 Visual Basic 14+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 如可能，更倾向使用 null 条件运算符。| **C#：** <br>`var v = o?.ToString();` <br><br> **Visual Basic：** <br> `Dim v = o?.ToString()`
| False | 如可能，更倾向使用三元 null 检查。 | **C#：** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic：** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="csharp_codestyle">CSharp 代码样式设置</a>
## <a name="var">“var”和显式类型</a>
### <a name="var_built_in">内置类型的“var”(IDE0007, IDE0008)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_for_built_in_types`| C# | true:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 更倾向在内置系统类型（如 `int`）中使用 `var`。| **C#：** <br>`var x = 5;`
| False | 更倾向在内置系统类型（如 `int`）中不使用 `var`。 | **C#：** <br>`int x = 5;`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
``` 

### <a name="var_apparent">类型为明显时的“var”(IDE0007, IDE0008)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_when_type_is_apparent`| C# | true:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 声明表达式右侧已提到该类型时更倾向使用 `var`。| **C#：** <br>`var obj = new C();`
| False | 声明表达式右侧已提到该类型时更倾向不使用 `var`。 | **C#：** <br>`C obj = new C();`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_var_when_type_is_apparent = true:suggestion
``` 

### <a name="var_elsewhere">其他位置 的“var”(IDE0007, IDE0008)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_elsewhere`| C# | true:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 在所有情况下更倾向使用 `var`，除非被另一个代码样式规则重写。| **C#：** <br>`var f = this.Init();`
| False | 在所有情况下更倾向不使用“var”，除非被另一个代码样式规则重写。| **C#：** <br>`bool f = this.Init();`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_var_elsewhere = true:suggestion
``` 

##<a name="expression_bodied_members">Expression-bodied 成员</a>
### <a name="expression_bodied_members_methods">方法 (IDE0022)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_methods`| C# 6.0+ | false:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 倾向于使用方法的 expression-bodied 成员。| **C#：** <br>`public int GetAge() => this.Age;`
| False | 倾向于不使用方法的 expression-bodied 成员。| **C#：** <br>`public int GetAge() { return this.Age; }`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
``` 

### <a name="expression_bodied_members_constructors">构造函数 (IDE0021)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_constructors`| C# 7.0+ | false:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 倾向于使用构造函数的 expression-bodied 成员。| **C#：** <br>`public Customer(int age) => Age = age;`
| False | 倾向于不使用构造函数的 expression-bodied 成员。| **C#：** <br>`public Customer(int age) { Age = age; }`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_constructors = false:none
``` 

### <a name="expression_bodied_members_operators">运算符 (IDE0023, IDE0024)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_operators` | C# 7.0+ | false:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 倾向于使用运算符的 expression-bodied 成员。| **C#：** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`=> new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);`
| False | 倾向于不使用运算符的 expression-bodied 成员。| **C#：** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_operators = false:none
``` 

### <a name="expression_bodied_members_properties">属性 (IDE0025)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_properties` | C# 7.0+ | true:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 倾向于使用属性的 expression-bodied 成员。| **C#：** <br>`public int Age => _age;`
| False | 倾向于不使用属性的 expression-bodied 成员。| **C#：** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = true:none
``` 

### <a name="expression_bodied_members_indexers">索引器 (IDE0026)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_indexers` | C# 7.0+ | true:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 倾向于使用索引器的 expression-bodied 成员。| **C#：** <br>`public T this[int i] => _value[i];`
| False | 倾向于不使用索引器的 expression-bodied 成员。| **C#：** <br>`public T this[int i] { get { return _values[i]; } }`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_indexers = false:none
``` 

### <a name="expression_bodied_members_accessors">访问器 (IDE0027)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_accessors` | C# 7.0+ | true:none | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 倾向于使用访问器的 expression-bodied 成员。| **C#：** <br>`public int Age { get => _age; set => _age = value; }`
| False | 倾向于不使用访问器的 expression-bodied 成员。| **C#：** <br>`public int Age { get { return _age; } set { _age = value; } }`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_accessors = false:none
``` 

## <a name="pattern_matching">模式匹配</a>
### <a name="pattern_matching_is_cast">“is”和“cast”检查 (IDE0020)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_pattern_matching_over_is_with_cast_check` | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 倾向于使用模式匹配，而不是带类型强制转换的 `is` 表达式。| **C#：** <br>`if (o is int i) {...}`
| False | 倾向于使用带类型强制转换的 `is` 表达式，而不是模式匹配。| **C#：** <br>`if (o is int) {var i = (int)o; ... }`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
```

### <a name="pattern_matching_as_null">“as”和“null”检查 (IDE0019)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_pattern_matching_over_as_with_null_check` | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 倾向于使用模式匹配，而不是带 null 检查的 `as` 表达式，来确定内容是否为某个特定类型。| **C#：** <br>`if (o is string s) {...}`
| False | 倾向于使用带 null 检查的 `as` 表达式，而不是模式匹配，来确定内容是否为某个特定类型。| **C#：** <br>`var s = o as string; if (s != null) {...}`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

### <a name="inlined_variable_declarations">内联变量声明 (IDE0018)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_inlined_variable_declaration` | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 如可能，更倾向内联声明 `out` 变量。 | **C#：** <br>`if (int.TryParse(value, out int i) {...}`
| False | 如可能，更倾向显式声明 `out` 变量。| **C#：** <br>`int i; if (int.TryParse(value, out i) {...}`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```
## <a name="expression_level_csharp">表达式级首选项</a>
### <a name="expression_level_default">简化 `default` 表达式 (IDE0034)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_prefer_simple_default_expression` | C# 7.1+ | true:suggestion | Visual Studio 2017 v. 15.3 |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 首选 `default` 次选 `default(T)` | **C#：** <br>`void DoWork(CancellationToken cancellationToken = default){ ... }`
| False | 首选。 | **C#：** <br>`void DoWork(CancellationToken cancellationToken = default(CancellationToken)){ ... }`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
``` 

## <a name="null_checking">“null”检查首选项</a>
### <a name="null_checking_throw_expressions">Throw 表达式 (IDE0016)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_throw_expression`  | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 更倾向使用 throw 表达式而不是 throw 语句。 | **C#：** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | 更倾向使用 throw 语句而不是 throw 表达式。| **C#：** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="null_checking_conditional_delegate_calls">更倾向使用条件委托调用 (IDE0041)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_conditional_delegate_call`  | C# 6.0+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 调用 lambda 时，更倾向使用条件合并操作 (`?.`)，而不是执行 null 检查。 | **C#：** <br>`func?.Invoke(args);`
| False | 调用 lambda 前，更倾向执行 null 检查，而不是使用条件合并运算符 (`?.`)。| **C#：** <br>`if (func!=null) { func(args); }`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```

## <a name="code_block">代码块首选项</a>
### <a name="prefer_braces">首选大括号 (IDE0011)</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_prefer_braces`  | C#  | true:none | Visual Studio 2017 v. 15.3 |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 首选大括号 | **C#：** <br>`if (test) { this.Display(); }`
| False | 尽可能不使用大括号 | **C#：** <br>`if (test) this.Display();`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

# <a name="formatting">格式设置规则</a>
## <a name="overview"></a>概述
**规则格式：**
`options_name = false|true`

对于格式选项，必须指定“true”（更倾向此选项）或“false”（不倾向此选项），必须改为指定规则适用的条件时除外。

## <a name="net-formatting-options"></a>.NET 格式设置选项

- **[.NET 格式设置](#usings)**
    - [组织 Using](#usings)
        - [首先排序系统指令](#usings_sort_system_first)
- **[C# 格式设置](#newline)**
    - [新建行选项](#newline)
        - [在左大括号 (`{`) 前新建行](#newline_before_brace)
        - [在 `else` 前新建行](#newline_before_else)
        - [在 `catch` 前新建行](#newline_before_catch)
        - [在 `finally` 前新建行](#newline_before_finally)
        - [在对象初始值设定项中的成员前新建行](#newline_before_object)
        - [在匿名类型中的成员前新建行](#newline_before_anonymous)
        - [在查询表达式子句中的成员前新建行](#newline_before_query)
    - [缩进选项](#indent)
        - [缩进 `switch` Case 内容](#indent_switch)
        - [缩进 `switch` 标签](#indent_switch_labels)
        - [标签定位](#label)
    - [间距选项](#spacing)
        - [转换后空格](#space_after_cast)
        - [在控制流语句中的关键字后空格](#space_control_flow)
        - [在方法声明参数和列表括号之间空格](#space_parameter_list)
        - [在方法调用参数列表的括号内空格](#space_method_call)
        - [在其他选项的括号内空格](#space_other)
    - [换行选项](#wrapping)
        - [将语句和成员声明保留在同一行上](#wrapping_statement)
        - [将程序块保留在单个行上](#wrapping_block)

## <a name="usings">组织 Using</a>
### <a name="usings_sort_system_first">首先排序系统指令</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_sort_system_directives_first`  |  C# 和 Visual Basic | true | Visual Studio 2017 v. 15.3  |


| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 按字母顺序对 System.* using 排序并将其置于其他 using 前面。| **C#：** <br>`using System.Collections.Generic;`<br> `using System.Threading.Tasks;`<br> `using Octokit;`
| False | 对 using 的顺序没有要求 | **C#：** <br>`using System.Collections.Generic;`<br> `using Octokit;` <br> `using System.Threading.Tasks;`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# .NET formatting settings:
[*.cs, *.vb]
dotnet_sort_system_directives_first = true
``` 

# <a name="csharp_formatting">C# 格式设置</a>
## <a name="newline">新建行选项</a>
### <a name="newline_before_brace"> 在左大括号 (`{`) 前新建行</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_before_open_brace`  |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 描述 
| ------------- |:-------------|
| accessors、anonymous_methods、anonymous_types、control_blocks、events, indexers、lambdas、local_functions、methods、object_collection、properties、types。 （对于多个值，请用“,”分隔）。 | 对于给定表达式，需要将大括号置于新行（Allman 样式） |
| 全部 | 对于所有表达式，需要将大括号置于新行 (Allman) |
| 无 | 对于所有表达式，需要将大括号置于同一行 (K&R) |

#### <a name="applied"></a>已应用：
```csharp
// csharp_new_line_before_open_brace = all
void MyMethod() 
{
    if (...) 
    {
        ...
    }
}
```

```csharp
// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
``` 

### <a name="newline_before_else"> 在 `else` 前新建行</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_before_else` |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 描述 
| ------------- |:-------------|
| True | 将 `else` 语句置于新行。  |
| False | 将 `else` 语句置于同一行。  |

#### <a name="applied"></a>已应用：
```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}
```

```csharp
// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_else = true
``` 

### <a name="newline_before_catch"> 在 `catch` 前新建行</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_catch`|  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 描述 
| ------------- |:-------------|
| True | 将 `catch` 语句置于新行。  |
| False | 将 `catch` 语句置于同一行。 |

#### <a name="applied"></a>已应用：
```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}
```

```csharp
// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_catch = true
``` 

### <a name="newline_before_finally"> 在 `finally` 前新建行</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_finally`|  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 描述 
| ------------- |:-------------|
| True | 需要将 `finally` 语句置于右大括号后的新行。  |
| False | 需要将 `finally` 语句置于右大括号所在的同一行。  |

#### <a name="applied"></a>已应用：
```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}
```

```csharp
// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_finally = true
``` 

### <a name="newline_before_object"> 在对象初始值设定项中的成员前新建行</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_members_in_object_initializers`|  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 描述 
| ------------- |:-------------|
| True | 需要将对象初始值设定项的成员置于单独的行。  |
| False | 需要将对象初始值设定项的成员置于同一行。  |

#### <a name="applied"></a>已应用：
```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_object_initializers = true
``` 

### <a name="newline_before_anonymous"> 在匿名类型中的成员前新建行</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_members_in_anonymous_types` |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 描述 
| ------------- |:-------------|
| True | 需要将匿名类型的成员置于单独的行。  |
| False | 需要将匿名类型的成员置于同一行。  |

#### <a name="applied"></a>已应用：
```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_anonymous_types = true
``` 

### <a name="newline_before_query"> 在查询表达式子句中的成员前新建行</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_within_query_expression_clauses`  |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 描述 
| ------------- |:-------------|
| True | 要求将查询表达式子句的元素置于单独的行。  |
| False | 要求将查询表达式子句的元素置于同一行。  |

#### <a name="applied"></a>已应用：
```csharp
// csharp_new_line_within_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;
```

```csharp
// csharp_new_line_within_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_within_query_expression_clauses = true
``` 

## <a name="indent">缩进选项</a>
### <a name="indent_switch"> 缩进 `switch` Case 内容</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_indent_case_contents`  |  C#  | true | Visual Studio 2017 v. 15.3  |

| 值 | 描述 
| ------------- |:-------------|
| True | 缩进 `switch` case 内容  |
| False | 不缩进 `switch` case 内容 |

#### <a name="applied"></a>已应用：
```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}
```

```csharp
// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
``` 

### <a name="indent_switch_labels"> 缩进 `switch` 标签</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_indent_switch_labels`  |  C#  | true | Visual Studio 2017 v. 15.3  |

| 值 | 描述 
| ------------- |:-------------|
| True | 缩进 `switch` 标签  |
| False | 不缩进 `switch` 标签 |

#### <a name="applied"></a>已应用：
```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}
```

```csharp
// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_indent_switch_labels = true
``` 

### <a name="label">标签定位</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_indent_labels`  |  C#  | one_less | Visual Studio 2017 v. 15.3  |


| 值 | 描述 
| ------------- |:-------------|
| one_less | 将标签置于比当前上下文少一个缩进的位置 |
| no_change | 将标签置于与当前上下文相同的缩进位置 |

#### <a name="applied"></a>已应用：
```csharp
// csharp_indent_labels = one_less
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
error:
    throw new Exception(...);
}

```

```csharp
// csharp_indent_labels= no_change
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
    error:
    throw new Exception(...);
}
```

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_indent_labels = one_less
``` 

## <a name="spacing">间距选项</a>
### <a name="space_after_cast"> 转换后空格</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_after_cast` |  C#  | false | Visual Studio 2017 v. 15.3  |


| 值 | 说明 | 已应用 |
| ------------- |:-------------|:-------------|
| True | 转换和值之间需要空格  | **C#：** <br>`int y = (int) x;`
| False | 转换和值之间无需空格 | **C#：** <br>`int y = (int)x;`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
``` 

### <a name="space_control_flow"> 在控制流语句中的关键字后空格 </a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_after_keywords_in_control_flow_statements` |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 说明 | 已应用 |
| ------------- |:-------------|:-------------|
| True | 关键字后需要空格 | **C#：** <br>`for (int i;i<x;i++) { ... }`
| False | 关键字后无需空格 | **C#：** <br>`for(int i;i<x;i++) { ... }`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_keywords_in_control_flow_statements = true
``` 

### <a name="space_parameter_list"> 在方法声明参数和列表括号之间空格</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_between_method_declaration_parameter_list_parentheses` |  C#  | false | Visual Studio 2017 v. 15.3  |


| 值 | 说明 | 已应用 |
| ------------- |:-------------|:-------------|
| True | 关键字后需要空格 | **C#：** <br>`void Bark( int x ) { ... }`
| False | 关键字后无需空格 | **C#：** <br>`void Bark(int x) { ... }`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_declaration_parameter_list_parentheses = true
```

### <a name="space_method_call"> 在方法调用参数列表的括号内空格</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_space_between_method_call_parameter_list_parentheses` |  C#  | false | Visual Studio 2017 v. 15.3  |


| 值 | 说明 | 已应用 |
| ------------- |:-------------|:-------------|
| true | 在控制流语句的括号之间放置空格 | **C#：** <br>`MyMethod( argument );`
| false | 在表达式的括号之间放置空格 | **C#：** <br>`MyMethod(argument);`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_call_parameter_list_parentheses = control_flow_statements, type_casts
```  

### <a name="space_other"> 在其他选项的括号内空格</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_space_between_parentheses`  |  C#  | false | Visual Studio 2017 v. 15.3  |


| 值 | 说明 | 已应用 |
| ------------- |:-------------|:-------------|
| control_flow_statements | 在控制流语句的括号之间放置空格 | **C#：** <br>`for( int i;i<x;i++ ) { ... }`
| 表达式 | 在表达式的括号之间放置空格 | **C#：** <br>`var z = ( x * y ) - ( ( y - x ) * 3);`
| type_casts | 在类型转换中的括号之间放置空格 | **C#：**<br>`int y = ( int )x;`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_parentheses = control_flow_statements, type_casts
``` 

## <a name="wrapping">换行选项</a>
### <a name="wrapping_statement">将语句和成员声明保留在同一行上</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_preserve_single_line_statements`   |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 描述 |
| ------------- |:-------------|
| True | 将语句和成员声明保留在同一行上  | 
| False | 将语句和成员声明保留在不同行上 | 

#### <a name="applied"></a>已应用
```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";
```

```csharp
//csharp_preserve_single_line_statements = false
int i = 0; 
string name = "John";
```

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
``` 

### <a name="wrapping_block">将程序块保留在单个行上</a>
| **选项名称** | **适用的语言** | **Visual Studio 默认值** | **支持的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|   `csharp_preserve_single_line_blocks`    |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 描述 |
| ------------- |:-------------|
| True | 将程序块保留在单个行上 | 
| False | 将程序块保留在单独的行上 | 

#### <a name="applied"></a>已应用
```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }
```

```csharp
//csharp_preserve_single_line_blocks = false
public int MyProperty
{ 
    get; set;
}
```

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_blocks = true
``` 

# <a name="naming">命名约定</a>
## <a name="overview"></a>概述
**规则格式：**<br>
namingRuleTitle:<br>
`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.severity = none|suggestion|warning|error`<br>
<br>
symbolTitle:<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = class, struct, interface, enum, property, method, field, event, namespace, delegate, type_parameter`<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = public, internal, private, protected, protected_internal`<br>
`dotnet_naming_symbols.<symbolTitle>.required_modifiers = abstract, async, const, readonly, static`<br>
<br>
styleTitle:<br>
`dotnet_naming_style.<styleTitle>.capitalization = pascal_case|camel_case|first_word_upper|all_upper|all_lower`<br>
`dotnet_naming_style.<styleTitle>.required_prefix = string`<br>
`dotnet_naming_style.<styleTitle>.required_suffix = string`<br>
`dotnet_naming_style.<styleTitle>.word_separator = string`<br>

## <a name="writing-a-naming-convention"></a>编写命名约定
对于命名约定，必须指定“符号”“样式”和“严重性”。 命名约定应从最具体到最抽象排序。 遇到的第一个可应用规则将成为唯一应用的规则。 

### <a name="severity"></a>严重性
以下是命名样式规则 `none`、`silent`、`suggestion`、`warning`、`error` 的严重性的有效选项。

 `none` 和 `silent` 是同义词，表示不应向用户显示任何形式的指示。 下面介绍禁用此规则的效果。

 `suggestion` 意味着将向用户显示 Error List: 中的下列内容和 IDE 中的下列内容。 `suggestion` 严重性将允许运行命名规则，但它不会导致内部版本中断。

严重性 | 效果
------------ | -------------
无/静默 | 如未遵循此样式，不会向用户显示任何内容，但会以该样式生成代码生成功能。 
建议 | 如未遵循此样式，以建议形式向用户显示此样式（前两个字符下带点）。
警告 | 如未遵循此样式，显示编译器警告。
错误 | 如未遵循此样式，显示编译器错误。

### <a name="symbol-specification"></a>符号规范
标识应将命名规则应用于的具有哪个修饰符的什么符号以及处于何种可访问性级别。

|  选项名称 | `dotnet_naming_rule.<namingRuleTitle>.symbols` |
| ------------- |:-------------:|
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_kinds`
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities`
|  | `dotnet_naming_symbols.<symbolTitle>.required_modifiers`

| 符号 | 可访问性 | 修饰符
| ------------- |------------- |------------- |
| `*` | `*` |  `abstract` | 
| `class` | `public` |  `must_inherit` | `async` | 
| `struct` | `internal` (C#) /  | `const` | 
| `interface` | `friend` (Visual Basic) | `readonly` | 
| `enum` | `private`  | `static` | 
| `property` | `protected` | `shared` |
| `method` |`protected_internal` (C#) | |
| `field` | `protected_friend` (Visual Basic) | |
| `event` | | |
| `delegate` | | |


### <a name="style-specification"></a>样式规范
标识要应用于符号的命名样式。

|  选项名称 | `dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>` |
| ------------- |:-------------:|
|  | `dotnet_naming_style.<styleTitle>.capitalization`|
|  | `dotnet_naming_style.<styleTitle>.required_prefix`|
|  | `dotnet_naming_style.<styleTitle>.required_suffix`|
|  | `dotnet_naming_style.<styleTitle>.word_separator`|


| 样式 | 描述 |
| ------------- |:-------------:|
| 前缀 | 必须出现在标识符前面的所需字符。 |
| 后缀 | 必须出现在标识符后面的所需字符。 |
| 文字分隔符 | 标识符中文字之间的所需分隔符。 |
| 大写 |`pascal_case`, `camel_case`, `first_word_upper`, `all_upper`, `all_lower` | 


### <a name="example-naming-convention"></a>命名约定示例
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.symbols  = any_async_methods
dotnet_naming_rule.async_methods_end_in_async.style    = end_in_async
dotnet_naming_rule.async_methods_end_in_async.severity = suggestion

dotnet_naming_symbols.any_async_methods.applicable_kinds           = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers         = async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization  = pascal_case
``` 

