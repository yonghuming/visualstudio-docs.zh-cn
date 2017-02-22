---
title: "使用 T4 文本模板的运行时文本生成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "“预处理文本模板”项目项"
  - "文本模板, 在运行时生成文件"
  - "文本模板, TransformText() 方法"
  - "TextTemplatingFilePreprocessor 自定义工具"
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 22
caps.handback.revision: 22
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 使用 T4 文本模板的运行时文本生成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以通过在您的应用程序在运行时生成文本字符串[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]运行时文本模板。  执行应用程序的计算机不必具有 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  运行库模板有时称为"预处理文本模板"由于在编译时，该模板会生成运行时执行的代码。  
  
 每个模板都包含将显示在生成的字符串中的文本和程序代码的片段。  程序片段为字符串的可变部分提供值，还控制条件部分和重复部分。  
  
 例如，以下模板可用于创建 HTML 报告的应用程序。  
  
```  
<#@ template language="C#" #>  
<html><body>  
<h1>Sales for Previous Month</h2>  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
This report is Company Confidential.  
</body></html>  
```  
  
 请注意，该模板是 HTML 页，其中可变部分已经替换为程序代码。  设计此类页面时可以先编写 HTML 页的静态原型。  然后，可以用程序代码替换表和其他可变部分，以便生成各个时刻有所变化的内容。  
  
 通过在应用程序中使用模板，可以查看输出的最终形式，比在一长串写入语句中查看更为方便。  更改输出的形式更方便且更可靠。  
  
## 可在任何应用程序中创建运行时文本模板  
  
#### 创建运行时文本模板  
  
1.  在解决方案资源管理器中，您的项目的快捷菜单上选择**添加**， **新项**。  
  
2.  在**添加新项** 对话框中，选择 **运行时文本模板**。  （在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的**“常用项\\常规”**下查看。）  
  
3.  键入模板文件的名称。  
  
    > [!NOTE]
    >  模板文件名将在生成的代码中用作类名。  因此，该名称不应包含空格或标点。  
  
4.  选择**添加**。  
  
     将创建一个扩展名为 **.tt** 的新文件。  该文件的**“自定义工具”**属性设置为 **TextTemplatingFilePreprocessor**。  它包含以下行：  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## 将现有文件转换为运行时模板  
 转换输出的现有示例是一种很好的模板创建方式。  例如，如果应用程序将生成 HTML 文件，则可以从创建纯 HTML 文件开始。  请确保该文件能正常运行，并且外观正确。  然后，将该文件包含在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目中，并将它转换为模板。  
  
#### 将现有文本文件转换为运行时模板  
  
1.  将该文件包含在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目中。  在解决方案资源管理器中的项目，在快捷菜单上选择**添加**， **现有项**。  
  
2.  将该文件的**“自定义工具”**属性设置为 **TextTemplatingFilePreprocessor**。  在解决方案资源管理器中的文件，请在快捷菜单上选择**属性**。  
  
    > [!NOTE]
    >  如果已经设置该属性，请确保该属性为 **TextTemplatingFilePreprocessor** 而不是 **TextTemplatingFileGenerator**。  如果将扩展名为 **.tt** 的文件包含在项目中，则可能出现上述情况。  
  
3.  将文件扩展名更改为 **.tt**。  虽然此步骤是可选的，但它有助于避免在不适当的编辑器中打开该文件。  
  
4.  从文件名的主要部分中删除所有空格或标点。  例如，“My Web Page.tt”是错误的，但“MyWebPage.tt”是正确的。  文件名将在生成的代码中用作类名。  
  
5.  在文件开头插入下面的行。  如果使用的是 Visual Basic 项目，请将“C\#”替换为“VB”。  
  
     `<#@ template language="C#" #>`  
  
## 运行时模板的内容  
  
### 模板指令  
 将模板第一行保留为您创建该文件时的样子：  
  
 `<#@ template language="C#" #>`  
  
 语言参数取决于项目的语言。  
  
### 纯文本内容  
 编辑 **.tt** 文件，使之包含应用程序要生成的文本。  例如：  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### 嵌入式程序代码  
 在 `<#` 和 `#>` 之间，可以插入程序代码。  例如：  
  
```c#  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb#  
<table>  
<#  
    For i As Integer = 1 To 10  
#>  
    <tr><td>Test name <#= i #> </td>  
      <td>Test value <#= i*i #> </td></tr>  
<#  
    Next  
#>  
</table>  
  
```  
  
 请注意，应在 `<# ... #>` 之间插入语句，应在 `<#= ... #>` 之间插入表达式。  有关更多信息，请参见[编写 T4 文本模板](../modeling/writing-a-t4-text-template.md)。  
  
## 使用模板  
  
### 从模板生成的代码  
 保存 **.tt** 文件时，将生成附属的 **.cs** 或 **.vb** 文件。  若要在解决方案资源管理器查看此文件，请展开 **.tt** 文件节点。  在 Visual Basic 项目中，单击解决方案资源管理器工具栏中的**“显示所有文件”**之后，可以展开该节点。  
  
 请注意，此附属文件包含一个分部类，该类包含一个名为 `TransformText()` 的方法。  此方法可以从应用程序中调用。  
  
### 在运行时生成文本  
 在应用程序代码中，可以通过调用生成模板内容，如下所示：  
  
```c#  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb#  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 若要在特定命名空间中放置已生成的类，请设置文本模板文件的**“自定义工具命名空间”**属性。  
  
### 调试运行时文本模板  
 调试和测试运行时文本模板普通代码的方式相同。  
  
 您可以在文本模板中设置断点。  如果在 Visual Studio 中的调试模式下启动应用程序，可以逐句通过代码，并按常规方式评估监视表达式。  
  
### 在构造函数中传递参数  
 通常，模板必须从应用程序的其他部分导入一些数据。  为便于实现此过程，由模板生成的代码以分部类的形式编写。  可以在项目的另一个文件中创建同一个类的其他部分。  该文件可以包含一个带参数的构造函数、若干属性和函数，这些内容可由模板中嵌入的代码和应用程序的其余部分访问。  
  
 例如，可以创建一个单独的文件 **MyWebPageCode.cs**：  
  
```c#  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 在模板文件 **MyWebPage.tt** 中，可以编写：  
  
```c#  
<h2>Sales figures</h2>  
<table>  
<# foreach (MyDataItem item in m_data.Items)   
   // m_data is declared in MyWebPageCode.cs  
   { #>  
      <tr><td> <#= item.Name #> </td>  
          <td> <#= item.Value #> </td></tr>  
<# } // end of foreach  
#>  
</table>  
```  
  
 在应用程序中使用此模板：  
  
```c#  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### Visual Basic 中的构造函数参数  
 在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中，单独的文件 **MyWebPageCode.vb** 包含：  
  
```vb#  
Namespace My.Templates  
  Partial Public Class MyWebPage  
    Private m_data As MyData  
    Public Sub New(ByVal data As MyData)  
      m_data = data  
    End Sub  
  End Class  
End Namespace  
```  
  
 模板文件可能包含：  
  
```vb#  
<#@ template language="VB" #>  
<html><body>  
<h1>Sales for January</h2>  
<table>  
<#  
    For Each item In m_data.Items  
#>  
    <tr><td>Test name <#= item.Name #> </td>  
      <td>Test value <#= item.Value #> </td></tr>  
<#  
    Next  
#>  
</table>  
This report is Company Confidential.  
</body></html>  
  
```  
  
 将通过在构造函数中传递参数来调用模板：  
  
```vb#  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### 在模板属性中传递数据  
 将数据传递到模板的另一种方法是向分部类定义中的模板类添加公共属性。  应用程序可以在调用 `TransformText()` 之前设置这些属性。  
  
 还可以在分部定义中向模板类添加字段。  这将使您能够在模板的连续执行之间传递数据。  
  
### 使用分部类编写代码  
 许多开发人员希望避免在模板内编写较大的代码体。  而应在与模板文件具有相同名称的分部类中定义方法。  然后从模板调用这些方法。  通过这种方式，模板可以更清晰地显示目标输出字符串的外观。  有关结果外观的讨论可以与创建结果所显示的数据的逻辑分开。  
  
### 程序集和引用  
 如果希望模板代码引用 .NET 或其他程序集（如 **System.Xml.dll**），应以常规方式将其添加到项目的**“引用”**中。  
  
 如果要以与 `using` 语句相同的方式导入命名空间，可以使用 `import` 指令：  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 这些指令必须紧随 `<#@template` 指令，置于文件开头。  
  
### 共享内容  
 如果要在几个模板间共享文本，可以将文本放置在一个单独的文件中，然后在需要这些文本的每个文件中包含这些文本：  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 包含的内容可以是程序代码和纯文本的任意组合，也可以是其他包含指令和其他指令。  
  
 在模板文件或已包含文件的文本中的任何位置，都可以使用包含指令。  
  
### 运行时文本模板之间的继承  
 可以通过编写基类模板（可以是抽象模板）在运行时模板之间共享内容。  使用`inherits`参数的`<@#template#>`指令以引用另一个运行库的模板类。  
  
#### 继承模式：基方法中的片段  
 在用于后面示例的模式中，请注意以下几点：  
  
-   基类 `SharedFragments` 在类功能块 `<#+ ... #>` 中定义方法。  
  
-   该基类不包含任何自由文本，  相反，其所有文本块都出现在类功能方法内。  
  
-   派生类可调用 `SharedFragments` 中定义的方法。  
  
-   应用程序调用派生类的 `TextTransform()` 方法，但不转换基类 `SharedFragments`。  
  
-   基类和派生类的运行时文本模板： 即， **自定义工具** 属性设置为  **TextTemplatingFilePreprocessor**。  
  
 **SharedFragments.tt：**  
  
```c#  
<#@ template language="C#" #>  
<#+  
protected void SharedText(int n)  
{  
#>  
   Shared Text <#= n #>  
<#+  
}  
// Insert more methods here if required.  
#>  
  
```  
  
 **MyTextTemplate1.tt：**  
  
```c#  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs：**  
  
```c#  
...   
MyTextTemplate1 t1  = new MyTextTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **结果输出：**  
  
```  
begin 1  
    Shared Text 2  
end 1  
```  
  
#### 继承模式：基体中的文本  
 在用来使用模板继承的此替代方法中，在基模板中定义大部分文本。  派生模板提供适合基内容的数据和文本片段。  
  
 **AbstractBaseTemplate1.tt：**  
  
```c#  
<#@ template language="C#" #>  
  
Here is the description for this derived template:  
  <#= this.Description #>  
  
Here is the fragment specific to this derived template:  
<#   
  this.PushIndent("  ");  
  SpecificFragment(42);   
  this.PopIndent();  
#>  
End of common template.  
<#+   
  // State set by derived class before calling TextTransform:  
  protected string Description = "";  
  // 'abstract' method to be defined in derived classes:  
  protected virtual void SpecificFragment(int n) { }  
#>  
  
```  
  
 **DerivedTemplate1.tt：**  
  
```c#  
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>  
<#   
  // Set the base template properties:  
  base.Description = "Description for this derived class";   
  
  // Run the base template:  
  base.TransformText();  
  
#>  
End material for DerivedTemplate1.  
  
<#+  
// Provide a fragment specific to this derived template:  
  
protected override void SpecificFragment(int n)  
{  
#>  
   Specific to DerivedTemplate1 : <#= n #>  
<#+  
}  
#>  
  
```  
  
 **应用程序代码：**  
  
```c#  
...   
DerivedTemplate1 t1 = new DerivedTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **结果输出：**  
  
```  
Here is the description for this derived template:  
  Description for this derived class  
  
Here is the fragment specific to this derived template:  
     Specific to DerivedTemplate1 : 42  
End of common template.  
End material for DerivedTemplate1.  
```  
  
## 相关主题  
 设计时模板：如果要使用模板生成将成为应用程序一部分的代码，请参见[使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
 运行时可以使用模板中的任何应用程序已确定的模板和它们的内容，在编译时。  但是，如果要编写 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 扩展，以便从在运行时更改的模板生成文本，请参见[在 VS 扩展中调用文本转换](../modeling/invoking-text-transformation-in-a-vs-extension.md)。  
  
## 请参阅  
 [代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)   
 [编写 T4 文本模板](../modeling/writing-a-t4-text-template.md)   
 [了解 T4： 预处理文本模板由 Oleg Sych](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)