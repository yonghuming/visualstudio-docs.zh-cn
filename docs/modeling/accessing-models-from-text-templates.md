---
title: "从文本模板访问模型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, accessing models
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: "33"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 741fc8ac1ed4e0cc449c8010b71bd13a484933a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="accessing-models-from-text-templates"></a>从文本模板访问模型
通过使用文本模板，你可以创建报表文件、 源代码文件和其他基于域特定语言模型的文本文件。 有关文本模板的基本信息，请参阅[代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)。 文本模板时进行调试，DSL 在实验模式下将工作，并且还将在其部署 DSL 的计算机上工作。  
  
> [!NOTE]
>  当你创建 DSL 解决方案，示例文本模板 **\*.tt**调试的项目中生成文件。 当您更改的域类名称时，这些模板将不再起作用。 不过，它们包括你需要的基本指令，并提供可以更新以匹配 DSL 的示例。  
  
 若要从文本模板访问模型：  
  
-   设置的模板指令的继承属性<xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>。 这提供了访问到存储区。  
  
-   指定你想要访问 DSL 指令处理器。 这将加载 DSL 的程序集，以便可以在文本模板的代码中使用其域类、 属性和关系。 它还加载指定的模型文件。  
  
 A`.tt`调试项目中创建文件类似于下面的示例，当你创建一个新[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]DSL 最小语言模板中的解决方案。  
  
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
  
 请注意有关此模板的以下几点：  
  
-   域类、 属性和 DSL 定义中定义的关系，可以使用该模板。  
  
-   模板将在指定的模型文件加载`requires`属性。  
  
-   中的属性`this`包含的根元素。 在这里，你的代码可以导航到模型的其他元素。 属性的名称通常是与 DSL 的根域类相同。 在此示例中，设为 `this.ExampleModel`。  
  
-   尽管编写的代码片段所用的语言是 C#，你可以生成任何类型的文本。 或者可以在编写代码[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]属性添加`language="VB"`到`template`指令。  
  
-   若要调试模板，添加`debug="true"`到`template`指令。 该模板将在另一个实例中打开[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]如果发生异常。 如果你想要在代码中的特定点在调试器中中断，insert 语句`System.Diagnostics.Debugger.Break();`  
  
     有关详细信息，请参阅[调试 T4 文本模板](../modeling/debugging-a-t4-text-template.md)。  
  
## <a name="about-the-dsl-directive-processor"></a>有关 DSL 指令处理器  
 模板可以使用你在 DSL 定义中定义的域类。 这使通常会显示该模板的起点附近的指令。 在前面的示例中，如下所示。  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 该指令的名称 ( `MyLanguage`，在此示例中) 的 DSL 名称派生。 它将调用*指令处理器*生成作为 DSL 的一部分。 你可以找到其源代码**Dsl\GeneratedCode\DirectiveProcessor.cs**。  
  
 DSL 指令处理器执行两个主要任务：  
  
-   它有效地将程序集和导入指令插入引用 DSL 的模板。 这允许你使用你的域类中的模板代码。  
  
-   它将加载在指定的文件。`requires`参数，并将属性设置`this`加载的模型的根元素的引用。  
  
## <a name="validating-the-model-before-running-the-template"></a>在运行该模板之前验证模型  
 你可能会导致之前执行模板要验证的模型。  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 请注意：  
  
1.  `filename`和`validation`分离的参数";"，并且必须没有其他分隔符或空格。  
  
2.  验证类别列表中的确定将执行的验证方法。 应以分隔多个类别"&#124;"，并且必须没有其他分隔符或空格。  
  
 如果找到错误，则它将报告在错误窗口中，并且结果文件将包含一条错误消息。  
  
##  <a name="Multiple"></a>从文本模板访问多个模型  
  
> [!NOTE]
>  此方法允许你读取同一模板中的多个模型，但不支持 ModelBus 引用。 若要读取的 ModelBus 引用关联的模型，请参阅[文本模板中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。  
  
 如果你想要从相同的文本模板访问多个模型，则必须调用生成的指令处理器一次为每个模型。 必须指定每个模型中的文件名称`requires`参数。 您必须指定你想要用于中的根域类的名称`provides`参数。 必须指定不同的值`provides`中每个指令调用的参数。 例如，假定您有三个名为 Library.xyz、 School.xyz 和 Work.xyz 的模型文件。 从其进行访问相同的文本模板，你必须编写的内容类似的以下的三个指令调用。  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  此示例的代码适用于基于最少的语言解决方案模板的语言。  
  
 若要访问你的文本模板中的模型，您现在可以在下面的示例编写的代码相似的代码。  
  
```csharp  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## <a name="loading-models-dynamically"></a>动态加载模型  
 如果你想要确定在运行时加载的模型，则可以在程序代码中，而不是使用 DSL 特定指令动态加载模型文件。  
  
 但是，特定于 DSL 的功能之一是指令的导入 DSL 的命名空间，以便将模板代码可以使用该 DSL 中定义的域类。 由于未使用的指令，因此你必须添加**\<程序集 >**和**\<导入 >**可能加载的所有模型的指令。 这非常简单，如果您可以加载不同的模型是相同的 DSL 的所有实例。  
  
 若要加载该文件，最有效方法是使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ModelBus。 在典型方案中，文本模板将使用特定于 DSL 的指令以常用方式加载的第一个模型。 该模型将包含到另一个模型的 ModelBus 引用。 ModelBus 可用于打开被引用的模型和访问的特定元素。 有关详细信息，请参阅[文本模板中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。  
  
 在不太常用的方案中，你可能想要打开模型文件对其具有仅为文件名，并且其不可能在当前[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目。 在这种情况下，可以通过使用中所述的技术打开文件[如何： 从在程序代码中的文件打开模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)。  
  
## <a name="generating-multiple-files-from-a-template"></a>从模板生成多个文件  
 如果你想要生成多个文件-例如，若要在模型中，生成一个单独的文件的每个元素有几种可能的方法。 默认情况下，只有一个文件生成从每个模板文件中。  
  
### <a name="splitting-a-long-file"></a>拆分长文件名  
 在此方法中，你可以使用模板生成一个文件中，由分隔符分隔。 然后将文件拆分为各个部分。 有两个模板，一个用于生成单个文件，另一个用于将其拆分。  
  
 **LoopTemplate.t4**生成长的单个文件。 请注意，文件扩展名为".t4"，因为它不应处理直接单击**转换所有模板**。 此模板采用一个参数，它指定用于分隔段的分隔符字符串：  
  
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
  
 `LoopSplitter.tt`调用`LoopTemplate.t4`，，然后将生成的文件拆分为其片段。 请注意，此模板没有已建模的模板，因为它不会读取模型。  
  
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