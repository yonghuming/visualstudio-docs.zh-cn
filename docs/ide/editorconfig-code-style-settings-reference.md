---
title: "EditorConfig 的 .NET 代码样式设置 | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 01
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
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: a5b26ed093ed86c8c438b2024f69d371fde2de36
ms.lasthandoff: 03/27/2017

---

# <a name="net-code-style-settings-for-editorconfig"></a>EditorConfig 的 .NET 代码样式设置

## <a name="possible-values"></a>可能的值：

`options_name = false|true : none|suggestion|warning|error`

对于代码样式选项，必须指定“true”（选择此选项）或“false”（不选择此选项）、冒号 (`:`) 及严重性（`none`、`suggestion`、`warning` 或 `error`）。 严重性代表想在基本代码中应用的样式的强制级别。

严重性 | 效果
------------ | -------------
无 | 如未遵循此样式，不会向用户显示任何内容，但会以该样式生成代码生成功能。 
建议 | 如未遵循此样式，以建议形式向用户显示此样式（前两个字符下带点）。
警告 | 如未遵循此样式，显示编译器警告。
错误 | 如未遵循此样式，显示编译器错误。

## <a name="net-code-style-options"></a>.NET 代码样式选项

- [.NET 代码样式设置](#this_and_me)
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
- [CSharp 代码样式设置](#csharp_codestyle)
    - [“var”](#var)
        - [内置类型的“var”](#var_built_in)
        - [类型为明显时的“var”](#var_apparent)
        - [其他位置的“var”](#var_elsewhere)
    - [Expression-Bodied 成员](#expression_bodied_members)
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
    - [“null”检查首选项](#null_checking)
        - [Throw 表达式](#null_checking_throw_expressions)
        - [条件委托调用](#null_checking_conditional_delegate_calls)

## <a name="this_and_me">“This.”和“me.”限定</a>

### <a name="this_and_me_fields">字段</a>

|  选项名称 | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **适用的语言** | C# 和 Visual Basic

| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 更喜欢非静态方法中使用的所有非静态字段以 `this.` 开始（在 C# 中）或以 `Me.` 开始（在 Visual Basic 中）。 | **C#：** <br>`this.capacity = 0;` <br><br> **Visual Basic：**`Me.capacity = 0`
| False | 更喜欢非静态方法中使用的所有非静态字段不以 `this.` 开始（在 C# 中）或不以 `Me.` 开始（在 Visual Basic 中）。 | **C#：** <br>`capacity = 0;` <br><br> **Visual Basic：**`capacity = 0`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">属性</a>

|  选项名称 | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **适用的语言** | C# 和 Visual Basic

| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 更喜欢非静态方法中使用的所有非静态属性以 `this.` 开始（在 C# 中）或以 `Me.` 开始（在 Visual Basic 中）。| **C#：** <br>`this.ID = 0;` <br><br> **Visual Basic：**`Me.ID = 0`
| False | 更喜欢非静态方法中使用的所有非静态属性不以 `this.` 开始（在 C# 中）或不以 `Me.` 开始（在 Visual Basic 中）。 | **C#：** <br>`ID = 0;` <br><br> **Visual Basic：**`ID = 0`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```


### <a name="this_and_me_methods">方法</a>
|  选项名称 | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **适用的语言** | C# 和 Visual Basic

| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 更喜欢从非静态方法中调用的所有非静态方法以 `this.` 开始（在 C# 中）和以 `Me.` 开始（在 VB 中）。| **C#：** <br>`this.Display();` <br><br> **Visual Basic：**`Me.Display()`
| False | 更喜欢从非静态方法中调用的所有非静态方法不以 `this.` 开始（在 C# 中）和不以 `Me.` 开始（在 VB 中）。 | **C#：** <br>`Display();` <br><br> **Visual Basic：**`Display()`


#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">事件</a>
|  选项名称 | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **适用的语言** | C# 和 Visual Basic

| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 更喜欢从非静态方法中引用的所有非静态事件以 `this.` 开始（在 C# 中）和以 `Me.` 开始（在 VB 中）。| **C#：** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic：**`AddHandler Me.Elapsed, AddressOf Handler`
| False | 更喜欢从非静态方法中引用的所有非静态事件不以 `this.` 开始（在 C# 中）和不以 `Me.` 开始（在 VB 中）。 | **C#：** <br>`Elapsed += Handler;` <br><br> **Visual Basic：**`AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">语言关键字（int 和 string 等）与类型引用的框架类型名称</a>
### <a name="language_keywords_variables">局部变量、参数和成员</a>
|  选项名称 | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **适用的语言** | C# 和 Visual Basic

| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 对于局部变量、参数和类型成员，更喜欢具有语言关键字（用于表示它们）的类型（`int`、`double`、`float`、`short`、`long`、`decimal` 和 `string`），以使用关键字而不是类型名称（`Int32` 和 `Int64` 等）。| **C#：** <br>`private int _member;` <br><br> **Visual Basic：**`Private _member As Integer`
| False | 对于局部变量、参数和类型成员，更喜欢具有语言关键字（用于表示它们）的类型（`int`、`double`、`float`、`short`、`long`、`decimal` 和 `string`），以使用类型名称（`Int32` 和 `Int64` 等）而不是关键字。  | **C#：** <br>`private Int32 _member;` <br><br> **Visual Basic：**`Private _member As Int32`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">成员访问表达式</a>
|  选项名称 | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **适用的语言** | C# 和 Visual Basic

| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 每当在具有关键字表示形式的类型上使用成员访问表达式时选择关键字（`int`、`double`、`float`、`short`、`long`、`decimal` 和 `string`）。| **C#：** <br>`var local = int.MaxValue;` <br><br> **Visual Basic：**`Dim local = Integer.MaxValue`
| False | 每当在具有关键字表示形式的类型上使用成员访问表达式时选择类型名称（`int`、`double`、`float`、`short`、`long`、`decimal` 和 `string`）。 | **C#：** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic：**`Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">表达式级首选项</a>
### <a name="expression_level_object_initializers">对象初始值设定项</a>
|  选项名称 | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **适用的语言** | C# 和 Visual Basic

| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 在可能情况下，更倾向使用对象初始值设定项来初始化对象。| **C#：** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic：**`Dim c = New Customer() With { .Age = 21 }`
| False | 更倾向不使用对象初始值设定项来初始化对象。 | **C#：** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic：** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">集合初始值设定项</a>
|  选项名称 | `dotnet_style_collection_initializer` |
| ------------- |:-------------:|
| **适用的语言** | C# 和 Visual Basic

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

### <a name="expression_level_tuple_names">显式元组名称</a>
|  选项名称 | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **适用的语言** | C# 和 Visual Basic

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

### <a name="expression_level_null_checking">“null”检查中的合并表达式</a>
|  选项名称 | `dotnet_style_coalesce_expression` |
| ------------- |:-------------:|
| **适用的语言** | C# 和 Visual Basic

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

### <a name="expression_level_null_propogation">“null”检查中的 null 传播</a>
|  选项名称 | `dotnet_style_null_propagation` |
| ------------- |:-------------:|
| **适用的语言** | C# 和 Visual Basic

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
## <a name="var">“var”</a>
### <a name="var_built_in">内置类型的“var”</a>
|  选项名称 | `csharp_style_var_for_built_in_types` |
| ------------- |:-------------:|
| **适用的语言** | C#

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

### <a name="var_apparent">类型为明显时的“var”</a>
|  选项名称 | `csharp_style_var_when_type_is_apparent` |
| ------------- |:-------------:|
| **适用的语言** | C#

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

### <a name="var_elsewhere">其他位置的“var”</a>
|  选项名称 | `csharp_style_var_elsewhere` |
| ------------- |:-------------:|
| **适用的语言** | C#

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

### <a name="expression_bodied_members">方法</a>
|  选项名称 | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **适用的语言** | C#

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

### <a name="expression_bodied_members_constructors">构造函数</a>
|  选项名称 | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **适用的语言** | C#

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

### <a name="expression_bodied_members_operators">运算符</a>
|  选项名称 | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **适用的语言** | C#

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

### <a name="expression_bodied_members_properties">属性</a>
|  选项名称 | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **适用的语言** | C#

| 值 | 说明 | 已应用 
| ------------- |:-------------|:-------------|
| True | 倾向于使用属性的 expression-bodied 成员。| **C#：** <br>`public int Age => _age;`
| False | 倾向于不使用属性的 expression-bodied 成员。| **C#：** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>editorconfig 文件示例：
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = false:none
``` 

### <a name="expression_bodied_members_indexers">索引器</a>
|  选项名称 | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **适用的语言** | C#

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

### <a name="expression_bodied_members_accessors">访问器</a>
|  选项名称 | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **适用的语言** | C#

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
### <a name="pattern_matching_is_cast">“is”和“cast”检查</a>
|  选项名称 | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **适用的语言** | C#

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

### <a name="pattern_matching_as_null">“as”和“null”检查</a>
|  选项名称 | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **适用的语言** | C#

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

### <a name="inlined_variable_declarations">内联变量声明</a>
|  选项名称 | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **适用的语言** | C#

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

## <a name="null_checking">“null”检查首选项</a>
### <a name="null_checking_throw_expressions">Throw 表达式</a>
|  选项名称 | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **适用的语言** | C#

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

### <a name="null_checking_conditional_delegate_calls">更倾向使用条件委托调用</a>
|  选项名称 | `csharp_style_conditional_delegate_call` |
| ------------- |:-------------:|
| **适用的语言** | C#

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

