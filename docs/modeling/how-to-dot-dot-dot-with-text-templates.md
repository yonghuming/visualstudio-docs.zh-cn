---
title: "如何使用文本模板...|Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: "11"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 93b4d129cd09fe3d3b67bfc743286577b1e285dd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to--with-text-templates"></a>如何：使用文本模板 ... 
中的文本模板[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]提供生成任何类型的文本的有效方法。 文本模板可用于在你的应用程序的一部分运行时和设计时生成你的项目代码的一些生成文本。 本主题总结了将最常要求"如何实现...？" 问题。  
  
 本主题中前面是项目符号的多个答案是替代建议。  
  
 文本模板的常规介绍，阅读[代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)。  
  
## <a name="how-to-"></a>如何。。。  
  
### <a name="generate-part-of-my-application-code"></a>生成我的应用程序代码的一部分  
 我有一种配置或*模型*文件或数据库中。 我的代码的一个或多个部件取决于该模型。  
  
-   从文本模板生成的某些代码文件。 有关详细信息，请参阅[使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)和[若要开始编写模板的最佳方法是什么？](#starting)。  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>在运行时，将数据传递到模板中生成文件  
 在运行时，我的应用程序生成文本的文件，如包含混合使用标准文本和数据的报表。 我想要避免编写数百个`write`语句。  
  
-   将运行时文本模板添加到你的项目。 此模板创建一个类，在代码中，你可以实例化和用于生成文本。 在构造函数参数，可以将数据传递给它。 有关详细信息，请参阅[使用 T4 文本模板的运行时文本生成](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
-   如果你想要从仅在运行时提供的模板生成，你可以使用标准文本模板。 如果你正在编写[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]扩展，你可以调用文本模板化服务。 有关详细信息，请参阅[在 VS 扩展中调用文本转换](../modeling/invoking-text-transformation-in-a-vs-extension.md)。 在其他上下文中，你可以使用文本模板化引擎。 有关更多信息，请参见<xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>。  
  
     使用\<#@parameter#> 指令将参数传递给这些模板。 有关详细信息，请参阅[T4 参数指令](../modeling/t4-parameter-directive.md)。  
  
### <a name="read-another-project-file-from-a-template"></a>从模板中读取另一个项目文件  
 读取文件来自同一[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]作为模板的项目：  
  
-   将 `hostSpecific="true"` 插入 `<#@template#>` 指令。  
  
     在代码中，使用`this.Host.ResolvePath(filename)`获取文件的完整路径。  
  
### <a name="invoke-methods-from-a-template"></a>从模板调用方法  
 如果方法中已存在，例如，标准[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]类：  
  
-   使用\<#@assembly#> 指令来加载程序集，并使用\<#@import#> 若要设置的命名空间上下文。 有关详细信息，请参阅[T4 导入指令](../modeling/t4-import-directive.md)。  
  
     如果你经常使用相同的一组程序集并导入指令，应考虑编写指令处理器。 在每个模板，你可以调用指令处理器，它可以加载程序集和模型文件和设置的命名空间上下文。 有关详细信息，请参阅[创建自定义 T4 文本模板指令处理器](../modeling/creating-custom-t4-text-template-directive-processors.md)。  
  
 如果你要自行编写方法：  
  
-   如果你正在编写的运行时文本模板，编写一个具有同名的运行时文本模板的分部类定义。 将其他方法添加到此类。  
  
-   写入到类功能控制块`<#+ ... #>`在方法、 属性和私有类可以声明的其中。 编译后的文本模板，它将转换为一个类。 标准控制块`<#...#>`和文本转换为单一的方法和类功能块插入作为单独的成员。 有关详细信息，请参阅[文本模板控制块](../modeling/text-template-control-blocks.md)。  
  
     定义为类功能还可以包含嵌入的文本块的方法。  
  
     考虑将放在单独的文件，您可以在类功能`<#@include#>`到一个或多个模板文件。  
  
-   在单独的程序集 （类库） 中编写方法，并从你的模板调用它们。 使用`<#@assembly#>`指令加载程序集，和`<#@import#>`设置的命名空间上下文。 请注意，若要在调试时，重新生成程序集，你可能拥有停止并重新启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 有关详细信息，请参阅[T4 文本模板指令](../modeling/t4-text-template-directives.md)。  
  
### <a name="generate-many-files-from-one-model-schema"></a>从一个模型架构生成多个文件  
 如果你通常从具有相同的 XML 或数据库架构的模型生成文件：  
  
-   应考虑编写指令处理器。 这使你可以将多个程序集语句和导入每个模板中具有一条自定义指令的语句。 指令处理器可以加载和分析模型文件。 有关详细信息，请参阅[创建自定义 T4 文本模板指令处理器](../modeling/creating-custom-t4-text-template-directive-processors.md)。  
  
### <a name="generate-files-from-a-complex-model"></a>从复杂的模型生成文件  
  
-   请考虑创建域特定语言 (DSL) 来表示该模型。 这样可以更轻松地编写一些模板，因为你使用的类型和属性来反映你的模型中的元素的名称。 无需分析该文件，或浏览 XML 节点。 例如:   
  
     `foreach (Book book in this.Library) { ... }`  
  
     有关详细信息，请参阅[Getting Started with 域特定语言](../modeling/getting-started-with-domain-specific-languages.md)和[从域特定语言生成代码](../modeling/generating-code-from-a-domain-specific-language.md)。  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>从获取数据[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 若要使用中提供的服务[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，集`hostSpecific`特性并加载`EnvDTE`程序集。 例如：  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#  
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));  
#>  
  
Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>  
  
```  
  
### <a name="execute-text-templates-in-the-build-process"></a>在生成过程中执行文本模板  
  
-   有关详细信息，请参阅[生成过程中的代码生成](../modeling/code-generation-in-a-build-process.md)。  
  
## <a name="more-general-questions"></a>更多常规问题  
  
###  <a name="starting"></a>若要开始编写文本模板的最佳方法是什么？  
  
1.  写入生成的文件的特定示例。  
  
2.  将其转换文本模板的方法是插入`<#@template #>`指令，和的指令和代码，加载输入的文件或模型所需。  
  
3.  渐进式将文件的部分替换为表达式和代码块。  
  
### <a name="what-is-a-model"></a>"模型"是什么？  
  
-   由模板读取的输入。 它可能是在文件或数据库中。 它可能是 XML，Visio 绘图时，或域特定语言 (DSL) 或 UML 模型，或它可能是纯文本。 它可以分布到多个文件。 通常多个模板都可以读取一个模型。  
  
     术语"模型"的含义是业务的，它表示你更直接比生成的程序代码或其他文件的某些方面。 例如，它可能表示你生成的软件将监督通信网络的计划。  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>使用文本模板的好处是什么？  
 通常情况下，你从一个模型生成多个代码或其他文件。 模型生成的代码比更能直接表示需求。 它省略实现详细信息，并以要求，而不是代码形式编写。 在需求更改-它们通常所执行的操作-时可以更新模型，更容易且更可靠比程序代码的不同部分。  
  
 因此，代码生成是从 agile 开发方法的角度的重要工具。  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>"最佳做法"还有哪些适用于文本模板？  
  
-   有关详细信息，请参阅[T4 文本模板编写准则](../modeling/guidelines-for-writing-t4-text-templates.md)。  
  
### <a name="what-is-t4"></a>什么是"T4"？  
  
-   另一个名称[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]此处所述的文本模板功能。 以前的版本，未发布，已"文本模板转换"的缩写。
