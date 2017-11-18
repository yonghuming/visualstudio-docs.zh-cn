---
title: "使用 T4 文本模板的运行时文本生成 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: "22"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 9dfcba23b9c8df3bbd62a0ef4dd0c4d98f578514
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>使用 T4 文本模板的运行时文本生成
你可以在运行时应用程序中生成文本字符串，通过使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]运行时文本模板。 执行应用程序的计算机不必具有[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 运行时模板有时被称为"预处理文本模板"，因为在编译时，该模板会生成在运行时执行的代码。  
  
 每个模板都混合的文本将出现在生成的字符串，并且程序代码的片段。 程序片段提供值的变量部分的字符串，并还控制条件和重复部分。  
  
 例如，无法创建 HTML 报告的应用程序中使用以下模板。  
  
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
  
 请注意该模板是 HTML 页，在其中的变量部分已替换为与程序代码。 您可以通过编写 HTML 页的静态原型开始这样的页的设计。 则无法将表和其他变量的部分替换到下一次从生成变化的内容的程序代码。  
  
 在应用程序中使用模板是更轻松地查看输出的最终形式，不是你可以在中，例如，写入语句一长串。 对输出的形式进行更改会更加容易、 更可靠。  
  
## <a name="creating-a-run-time-text-template-in-any-application"></a>在任何应用程序中创建运行时文本模板  
  
#### <a name="to-create-a-run-time-text-template"></a>若要创建运行时文本模板  
  
1.  在解决方案资源管理器，你的项目的快捷菜单上选择**添加**，**新项**。  
  
2.  在**添加新项**对话框中，选择**运行时文本模板**。 (在[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]下方查看**常见 Items\General**。)  
  
3.  键入你的模板文件的名称。  
  
    > [!NOTE]
    >  模板文件的名称将用作生成的代码中的类名称。 因此，它不应具有空格或标点。  
  
4.  选择“添加”。  
  
     创建新的文件具有扩展名**.tt**。 其**自定义工具**属性设置为**TextTemplatingFilePreprocessor**。 它包含以下行：  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## <a name="converting-an-existing-file-to-a-run-time-template"></a>将现有文件转换为运行时模板  
 创建模板一种好方法是将转换输出的现有示例。 例如，如果你的应用程序会生成 HTML 文件，你可以通过创建的纯 HTML 文件。 请确保它正常运行，并且其外观正确无误。 然后将其到包含你[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目，然后将其转换为模板。  
  
#### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>若要将现有的文本文件转换为运行时模板  
  
1.  将文件包括你[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目。 在解决方案资源管理器，从项目的快捷菜单上选择**添加**，**现有项**。  
  
2.  设置文件的**自定义工具**属性**TextTemplatingFilePreprocessor**。 在解决方案资源管理器，该文件的快捷菜单上选择**属性**。  
  
    > [!NOTE]
    >  如果已设置该属性，请确保它是**TextTemplatingFilePreprocessor**和 not **TextTemplatingFileGenerator**。 可能的原因是包含已具有扩展名的文件**.tt**。  
  
3.  更改到文件扩展名**.tt**。 虽然此步骤是可选的它可帮助你避免在不适当的编辑器中打开该文件。  
  
4.  从文件名称的主要部分中删除任何空格或标点。 例如，"我的 Web Page.tt"将是不正确，但是"MyWebPage.tt"正确。 文件名称将用作生成的代码中的类名称。  
  
5.  在文件的开头插入以下行。 如果你正在 Visual Basic 项目中，将"C#"与"VB"。  
  
     `<#@ template language="C#" #>`  
  
## <a name="the-content-of-the-run-time-template"></a>运行时模板的内容  
  
### <a name="template-directive"></a>模板指令  
 创建文件时保持模板的第一行：  
  
 `<#@ template language="C#" #>`  
  
 语言参数将取决于你的项目的语言。  
  
### <a name="plain-content"></a>纯文本内容  
 编辑**.tt**文件，以包含您的应用程序生成的文本。 例如:   
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### <a name="embedded-program-code"></a>嵌入的程序代码  
 你可以将插入程序代码之间`<#`和`#>`。 例如：  
  
```csharp  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb  
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
  
 请注意之间插入语句`<# ... #>`和表达式之间插入`<#= ... #>`。 有关详细信息，请参阅[编写 T4 文本模板](../modeling/writing-a-t4-text-template.md)。  
  
## <a name="using-the-template"></a>使用模板  
  
### <a name="the-code-built-from-the-template"></a>从模板生成的代码  
 每当保存**.tt**文件，分公司**.cs**或**.vb**将生成文件。 若要查看此文件在解决方案资源管理器中的，展开**.tt**文件节点。 在 Visual Basic 项目中，你将能够展开的节点，则在单击后**显示所有文件**解决方案资源管理器工具栏中。  
  
 请注意，此附属文件包含分部类，其中包含调用的方法`TransformText()`。 你可以从你的应用程序调用此方法。  
  
### <a name="generating-text-at-run-time"></a>在运行时生成文本  
 在应用程序代码中，你可以生成你的模板使用如下所示的内容：  
  
```csharp  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 若要在特定的命名空间中放置生成的类，将设置**自定义工具 Namespace**的文本模板文件的属性。  
  
### <a name="debugging-runtime-text-templates"></a>调试运行时文本模板  
 调试并测试运行时文本模板中为普通代码相同的方式。  
  
 文本模板中，可以设置断点。 如果在从 Visual Studio 的调试模式下启动应用程序，你可以单步执行代码并对监视表达式评估按照通常的方式。  
  
### <a name="passing-parameters-in-the-constructor"></a>在构造函数中传递参数  
 通常模板必须从应用程序的其他部分中导入一些数据。 要使这更加轻松，由模板生成的代码是一个分部类。 你的项目中，可以在另一个文件中创建相同的类的另一部分。 该文件可以包括参数、 属性和可以访问在模板中，嵌入的代码和应用程序的其余部分的函数的构造函数。  
  
 例如，可以创建一个单独的文件**MyWebPageCode.cs**:  
  
```csharp  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 模板文件中**MyWebPage.tt**，你可以编写：  
  
```csharp  
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
  
```csharp  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### <a name="constructor-parameters-in-visual-basic"></a>在 Visual Basic 中的构造函数参数  
 在[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，单独的文件**MyWebPageCode.vb**包含：  
  
```vb  
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
  
```vb  
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
  
 并将通过将参数传递的构造函数中调用模板：  
  
```vb  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### <a name="passing-data-in-template-properties"></a>在模板属性中传递数据  
 将数据传递给模板的另一种方法是将公共属性添加到分部类定义中的模板类。 你的应用程序可以在调用之前设置的属性`TransformText()`。  
  
 你还可以将字段添加到模板类中的部分定义。 这将使您的模板的连续执行之间传递数据。  
  
### <a name="use-partial-classes-for-code"></a>使用代码的分部类  
 许多开发人员希望避免编写模板中的较大的代码体。 相反，定义为模板文件具有相同名称的分部类中的方法。 从模板中调用这些方法。 这种方式，模板显示更清楚地了解哪些目标输出字符串将如下所示。 可以从创建它显示的数据的逻辑分隔讨论有关外观的结果。  
  
### <a name="assemblies-and-references"></a>程序集和引用  
 如果你想要模板代码如引用.NET 或其他程序集**System.Xml.dll**，应将其添加到你的项目的**引用**按常规方式。  
  
 如果你想要在相同的方式导入命名空间`using`语句，你可以执行此操作与`import`指令：  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 后立即，必须将这些指令放置在该文件，开始`<#@template`指令。  
  
### <a name="shared-content"></a>共享的内容  
 如果你有几个模板间共享的文本，你可以将其放在单独的文件，并将其包含在它应在其中显示每个文件：  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 包含的内容可以是程序代码和纯文本的任意组合，并且它可以包含其他 include 指令和其他指令。  
  
 Include 指令可以使用文本中的模板文件或包含的文件中的任意位置。  
  
### <a name="inheritance-between-run-time-text-templates"></a>运行时文本模板之间的继承  
 你可以共享通过编写才能是抽象的基的类模板的运行时模板之间的内容。 使用`inherits`参数`<@#template#>`指令以引用另一个运行时模板类。  
  
#### <a name="inheritance-pattern-fragments-in-base-methods"></a>继承模式： 基方法中的片段  
 在下面的示例中使用的模式，请注意以下几点：  
  
-   基类`SharedFragments`定义类功能块中的方法`<#+ ... #>`。  
  
-   基类中包含任何可用的文本。 相反，其所有文本块中都进行类功能方法。  
  
-   派生的类调用的方法中定义`SharedFragments`。  
  
-   应用程序调用`TextTransform()`方法的派生类中，但不转换基类`SharedFragments`。  
  
-   基类和派生类是运行时文本模板： 即**自定义工具**属性设置为**TextTemplatingFilePreprocessor**。  
  
 **SharedFragments.tt:**  
  
```csharp  
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
  
 **MyTextTemplate1.tt:**  
  
```csharp  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs:**  
  
```csharp  
...   
MyTextTemplate1 t1  = new MyTextTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **生成的输出：**  
  
```  
begin 1  
    Shared Text 2  
end 1  
```  
  
#### <a name="inheritance-pattern-text-in-base-body"></a>在基的正文中的继承模式： 文本  
 在使用模板继承此备用方法，在基模板中定义的文本的大容量。 派生的模板提供的数据和文本片段符合为基的内容。  
  
 **AbstractBaseTemplate1.tt:**  
  
```csharp  
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
  
 **DerivedTemplate1.tt:**  
  
```csharp  
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
  
```csharp  
...   
DerivedTemplate1 t1 = new DerivedTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **生成的输出：**  
  
```  
Here is the description for this derived template:  
  Description for this derived class  
  
Here is the fragment specific to this derived template:  
     Specific to DerivedTemplate1 : 42  
End of common template.  
End material for DerivedTemplate1.  
```  
  
## <a name="related-topics"></a>相关主题  
 设计时模板： 如果你想要使用模板生成代码，该按钮将变为应用程序的一部分，请参阅[使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
 运行时模板可在任何应用程序在编译时确定模板和它们的内容的位置。 但是，如果你想要编写[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]从模板在运行时更改，请参阅生成文本的扩展[在 VS 扩展中调用文本转换](../modeling/invoking-text-transformation-in-a-vs-extension.md)。  
  
## <a name="see-also"></a>另请参阅  
 [代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)   
 [编写 T4 文本模板](../modeling/writing-a-t4-text-template.md)   
 [通过 Oleg Sych 了解 T4： 已预处理的文本模板](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)