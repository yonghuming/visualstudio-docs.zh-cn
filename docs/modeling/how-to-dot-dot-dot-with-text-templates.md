---
title: "如何使用文本模板...|Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 11
author: alancameronwills
ms.author: awills
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: b874c9c259664f7f07e3266781909f74ece6e60a
ms.lasthandoff: 02/22/2017

---
# <a name="how-to--with-text-templates"></a>如何：使用文本模板 ... 
中的文本模板[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]提供有用的方法生成的任何类型的文本。 可以使用文本模板生成文本，作为您的应用程序的一部分运行时和设计时生成的某些项目代码。 本主题总结了最常问"我如何？..." 问题。  
  
 本主题中前面带有项目符号的多个答案是替代建议。  
  
 有关文本模板的常规介绍，阅读[代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)。  
  
## <a name="how-to-"></a>如何。。。  
  
### <a name="generate-part-of-my-application-code"></a>生成应用程序代码的一部分  
 我有一个配置或*模型*文件或数据库中。 我的代码的一个或多个部分取决于该模型。  
  
-   从文本模板生成的某些代码文件。 有关详细信息，请参阅[使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)和[若要开始编写模板的最佳方法是什么？](#starting)。  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>在运行时，将数据传递到该模板生成文件  
 在运行时，我的应用程序生成文本文件，例如包含多种标准文本和数据的报表。 我想要避免编写数百个`write`语句。  
  
-   将运行时文本模板添加到您的项目。 此模板创建一个类在代码中，您可以实例化并使用生成的文本。 在构造函数参数中，可以将数据传递给它。 有关详细信息，请参阅[使用 T4 文本模板的运行时文本生成](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
-   如果您想要从只能在运行时可用的模板生成，您可以使用标准文本模板。 如果您正在编写[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]扩展中，您可以调用文本模板化服务。 有关详细信息，请参阅[VS 扩展中调用文本转换](../modeling/invoking-text-transformation-in-a-vs-extension.md)。 在其他上下文中，您可以使用文本模板化引擎。 有关详细信息，请参阅<xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>。</xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>  
  
     使用\<#@parameter#&1;> 指令以将参数传递给这些模板。 有关详细信息，请参阅[T4 参数指令](../modeling/t4-parameter-directive.md)。  
  
### <a name="read-another-project-file-from-a-template"></a>从模板中读取另一个项目文件  
 来自同一个读取文件[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]作为模板的项目︰  
  
-   将 `hostSpecific="true"` 插入 `<#@template#>` 指令。  
  
     在代码中，使用`this.Host.ResolvePath(filename)`来获得该文件的完整路径。  
  
### <a name="invoke-methods-from-a-template"></a>从模板调用方法  
 如果这些方法中已存在，例如，标准[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]类︰  
  
-   使用\<#@assembly#&1;> 指令来加载该程序集，并使用\<#@import#&1;> 设置命名空间上下文。 有关详细信息，请参阅[T4 导入指令](../modeling/t4-import-directive.md)。  
  
     如果您经常使用相同的一组程序集并导入指令，应考虑编写指令处理器。 在每个模板，可以调用指令处理器，它可以加载这些程序集和模型文件和设置的命名空间上下文。 有关详细信息，请参阅[创建自定义 T4 文本模板指令处理器](../modeling/creating-custom-t4-text-template-directive-processors.md)。  
  
 如果您要自行编写方法︰  
  
-   如果您编写的运行时文本模板中，编写运行时文本模板同名的分部类定义。 添加到此类中的其他方法。  
  
-   编写类功能控制块`<#+ ... #>`在其中您可以将声明方法、 属性和私有类。 在编译时文本模板，它将转换为一个类。 标准控制块`<#...#>`和文本将转换为单一的方法和类功能块插入作为单独的成员。 有关详细信息，请参阅[文本模板控制块](../modeling/text-template-control-blocks.md)。  
  
     定义为类功能还可以包含嵌入的文本块的方法。  
  
     请考虑在单独的文件，您可以放置类功能`<#@include#>`放到一个或多个模板文件。  
  
-   在单独的程序集 （类库） 中编写方法，并从您的模板调用它们。 使用`<#@assembly#>`指令来加载该程序集和`<#@import#>`设置命名空间上下文。 请注意，为了在调试时，重新生成程序集，可能必须停止并重新启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 有关详细信息，请参阅[T4 文本模板指令](../modeling/t4-text-template-directives.md)。  
  
### <a name="generate-many-files-from-one-model-schema"></a>从一个模型架构中生成多个文件  
 如果您经常从具有相同的 XML 或数据库架构的模型生成文件︰  
  
-   应考虑编写指令处理器。 这使您以将程序集的多个语句和导入每个模板中具有单一的自定义指令的语句。 指令处理器可以加载和分析模型文件。 有关详细信息，请参阅[创建自定义 T4 文本模板指令处理器](../modeling/creating-custom-t4-text-template-directive-processors.md)。  
  
### <a name="generate-files-from-a-complex-model"></a>从复杂的模型生成文件  
  
-   请考虑创建域特定语言 (DSL) 来表示该模型。 这使得它更易于编写一些模板，因为您使用的类型和属性来反映在模型中元素的名称。 不需要分析该文件，或浏览 XML 节点。 例如:   
  
     `foreach (Book book in this.Library) { ... }`  
  
     有关详细信息，请参阅[域特定语言入门](../modeling/getting-started-with-domain-specific-languages.md)和[从域特定语言生成代码](../modeling/generating-code-from-a-domain-specific-language.md)。  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>从获取数据[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 若要使用中提供的服务[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，由集`hostSpecific`特性并加载`EnvDTE`程序集。 例如：  
  
```c#  
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
  
## <a name="more-general-questions"></a>更多一般问题  
  
###  <a name="a-namestartinga-what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a>若要开始编写文本模板的最佳方法是什么？  
  
1.  写入生成的文件的具体示例。  
  
2.  将其转换文本模板的方法是插入`<#@template #>`指令，指令和代码所需加载模型的输入的文件。  
  
3.  渐进式使用的表达式和代码块替换文件中的部分。  
  
### <a name="what-is-a-model"></a>"模型"是什么？  
  
-   由模板读取的输入。 它可以在文件或数据库中。 它可能是 XML 中，或 Visio 绘图时，域特定语言 (DSL) 或 UML 模型中，或者它可能是纯文本。 它可以分布在多个文件。 通常，多个模板读取一个模型。  
  
     术语"模型"的含义是业务的，它表示您更直接比生成的程序代码或其他文件的某些方面。 例如，它可能表示你生成的软件将监督通信网络的计划。  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>使用文本模板的好处是什么？  
 通常情况下，您从一个模型生成多个代码或其他文件。 模型比生成的代码更能直接表示要求。 它省略了实现细节，并按照要求，而不是代码编写。 在需求变化 – 人员通常都 – 时可以更新该模型，更容易且更可靠比程序代码的不同部分。  
  
 因此，代码生成是从敏捷开发方法的角度来看一个重要的工具。  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>"最佳实践"还有哪些适用于文本模板？  
  
-   有关详细信息，请参阅[T4 文本模板编写准则](../modeling/guidelines-for-writing-t4-text-templates.md)。  
  
### <a name="what-is-t4"></a>什么是"T4"？  
  
-   另一个名称[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]此处所述的文本模板功能。 以前的版本，未发布，是"文本模板转换"的缩写。

