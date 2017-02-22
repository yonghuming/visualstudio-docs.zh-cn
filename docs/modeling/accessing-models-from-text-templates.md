---
title: "从文本模板访问模型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文本模板, 访问模型"
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 33
caps.handback.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 从文本模板访问模型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用文本模板，可以创建报告文件、源代码文件和基于域特定语言模型中的其他文本文件。  有关文本模板的基本信息，请参见 [代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)。  文本模板在实验模式中工作，在调试 DSL 和还处理部署了 DSL 的计算机。  
  
> [!NOTE]
>  如果您创建一个 DSL 解决方案时，示例文本模板 **\*.tt** 文件在调试项目中生成的。  当您更改字段类的名称，这些模板将不再有效。  但是，它们由所需的基本指令，并提供可更新与 DSL 的示例。  
  
 对于从文本模板访问一个模型:  
  
-   设置模板指令的继承属性设置为 <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>。  这提供了对存储。  
  
-   为要访问的 DSL 指定指令处理器。  这将加载 DSL 的程序集，以便您在文本模板的代码可以使用其域类、属性和关系。  它还会加载您指定的模型文件。  
  
 ，当您创建从 DSL 最小的语言模板时，的新 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案 `.tt` 文件类似于下面的示例在调试项目创建。  
  
```  
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ output extension=".txt" #>  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
  
This text will be output directly.  
  
This is the name of the model: <#= this.ModelRoot.Name #>  
  
Here is a list of elements in the model:  
<#  
  // When you change the DSL Definition, some of the code below may not work.  
  foreach (ExampleElement element in this.ExampleModel.Elements)  
  {#>  
<#= element.Name #>  
<#      
  }  
#>  
  
```  
  
 以下几点此模板的通知:  
  
-   模板可以使用在 DSL 定义的域类、属性和关系。  
  
-   模板加载在 `requires` 属性指定的模型文件。  
  
-   在 `this` 的属性包含根元素。  因此，代码可以导航到模型中的其他元素。  属性的名称通常与 DSL 的根域类。  在此示例中，它是 `this.ExampleModel`。  
  
-   虽然代码零碎的语言编写是 C\#，可以生成任何类型的文本。  通过添加属性或者可以编写在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 的代码 `language="VB"` 到 `template` 指令。  
  
-   若要调试模板，请添加 `debug="true"` 到 `template` 指令。  如果发生异常，，该模板中 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 其他实例中打开。  如果要中断调试器中的特定点在代码中，插入语句 `System.Diagnostics.Debugger.Break();`  
  
     有关更多信息，请参见 [调试 T4 文本模板](../modeling/debugging-a-t4-text-template.md)。  
  
## 有关 DSL 指令处理器  
 模板可以使用在 DSL 定义的字段类。  这是在模板的开头。通常出现的指令实现。  在前面的示例中，它下面。  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 指令 \( `MyLanguage`的名称，在本例中为\) 从 DSL 的名称派生。  它调用作为 DSL 的一部分，生成的指令 *处理器* 。  可以查找其在 **Dsl\\GeneratedCode\\DirectiveProcessor.cs**的源代码。  
  
 DSL 指令处理器执行两个主要任务:  
  
-   活动会插入程序集和导入指令添加到引用 DSL 的模板中。  这在模板代码可以使用域类。  
  
-   它加载在 `requires` 参数指定的文件，然后将引用加载模块的根元素。 `this` 的属性。  
  
## 验证模型在运行之前模板  
 在模板中，前，可以使模型验证。  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 通知该:  
  
1.  `filename` 和 `validation` 参数用 “; ”并没有其他分隔符或空格。  
  
2.  验证类别列表将确定哪些验证方案中执行。  应分隔多个类别。 “&#124;”并没有其他分隔符或空格。  
  
 如果发现错误，在错误窗口中将报告，因此，结果文件将包含一条错误消息。  
  
##  <a name="Multiple"></a> 从文本模板访问的多个模型  
  
> [!NOTE]
>  此方法使您得以在同一模板的多个模型，但不支持 ModelBus 引用。  若要读取由 ModelBus 交互相联接的方式引用，请参见 [在文本模板中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。  
  
 如果要访问多从同一个文本模板的模型，必须调用所生成的指令处理器每个模型的一次。  在 `requires` 参数必须指定每个模型文件名。  必须指定要对根域类使用在 `provides` 参数的名称。  必须为 `provides` 参数指定不同的值在每个指令调用。  例如，假定，可以调用 Library.xyz、 School.xyz 和 Work.xyz 的三个模型文件。  访问类似于下面几节中的它们从同一个文本模板，必须编写三个指令调用。  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  此代码示例是基于最小语言解决方案模板的语言。  
  
 访问在文本模板中，您的模型现在可以编写代码类似于下面示例中的代码。  
  
```c#  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb#  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## 动态加载模块  
 如果要在建模加载的运行时，在程序代码中动态加载的模型文件，而不是将使用 DSL 特定指令。  
  
 但是，其中一个 DSL 特定指令的函数是导入 DSL 命名空间，因此，模板代码在该 DSL 可以使用定义的字段类。  由于不使用指令，必须添加 **\<assembly\>** 和 **\<import\>** 指令可以加载的所有设计的。  这是简单，如果您可能会加载不同的方式相同 DSL 的所有实例。  
  
 使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus，若要加载文件，最有效的方法。  在典型的方案中，文本模板在常规方式将使用一个 DSL 特定指令加载第一个模型。  模型将包含 ModelBus 引用另一个模型。  可以使用 ModelBus 引用打开模型和访问特定元素。  有关更多信息，请参见 [在文本模板中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。  
  
 在较长通常不方案，您可能需要打开您仅有一个文件名，并且，可能不在此 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目中的模型文件。  在这种情况下，可以使用打开该文件在 [如果：在程序代码中从文件打开模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)描述的技术。  
  
## 从模板生成的多文件  
 如果您希望生成多个文件 \(例如，为每个元素生成一个单独的文件中设计，有几种可能的方法。  默认情况下，只有一个文件从每个模板文件生成。  
  
### 拆分较长的文件  
 在此方法中，将使用一个模板都生成一个单独的文件中，用分隔符。  然后可以拆分了文件转换为其部件。  有两个模板，一个用于启动单文件以及其他拆分它。  
  
 **LoopTemplate.t4** 生成长的单文件。  通知其文件扩展名为 “.t4”，因为，不应直接对其进行处理，当您单击 **转换所有模板**。  此模板参数，指定分隔符符来分隔段:  
  
```  
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ parameter name="delimiter" type="System.String" #>  
<#@ output extension=".txt" #>  
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>  
<#  
  // Create a file segment for each element:  
  foreach (ExampleElement element in this.ExampleModel.Elements)   
  {   
    // First item is the delimiter:  
#>  
<#= string.Format(delimiter, element.Id) #>  
  
   Element: <#= element.Name #>  
<#  
   // Here you generate more content derived from the element.  
  }  
#>  
  
```  
  
 `LoopSplitter.tt` 调用 `LoopTemplate.t4`，然后拆分生成的文件转换为它的段。  请注意此模板不必是一个建模，模板，因为它不读取模型。  
  
```  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>  
<#@ import namespace="System.Runtime.Remoting.Messaging" #>  
<#@ import namespace="System.IO" #>  
  
<#  
  // Get the local path:  
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");  
  string dir = Path.GetDirectoryName(itemTemplatePath);  
  
  // Get the template for generating each file:  
  string loopTemplate = File.ReadAllText(itemTemplatePath);  
  
  Engine engine = new Engine();  
  
  // Pass parameter to new template:  
  string delimiterGuid = Guid.NewGuid().ToString();  
  string delimiter = "::::" + delimiterGuid + ":::";  
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");   
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);  
  
  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);  
  
  foreach (string nameAndFile in separateFiles)   
  {   
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;  
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);  
     if (parts.Length < 2) continue;  
#>  
 Generate: [<#= dir #>] [<#= parts[0] #>]  
<#  
     // Generate a file from this item:  
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);    
  }  
#>  
  
```