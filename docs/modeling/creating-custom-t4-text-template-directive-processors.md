---
title: "创建自定义 T4 文本模板指令处理器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 29
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
ms.translationtype: MT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: a8f56201528b15da04c5861be5c9afdd9a9b379e
ms.contentlocale: zh-cn
ms.lasthandoff: 08/17/2017

---
# <a name="creating-custom-t4-text-template-directive-processors"></a>创建自定义 T4 文本模板指令处理器
*文本模板转换过程*采用*文本模板*文件作为输入并生成一个文本文件作为输出。 *文本模板转换引擎*与文本模板转换宿主和一个或多个文本模板过程中和引擎进行交互的控件*指令处理器*完成该过程。 有关详细信息，请参阅[文本模板转换过程](../modeling/the-text-template-transformation-process.md)。  
  
 若要创建自定义指令处理器，需要创建一个从 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 继承的类。  
  
 这两个区别是，<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>实现从用户获取参数以及生成的代码生成模板输出文件时需要的最小接口。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>实现需要/提供设计模式。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>处理两个特殊参数，`requires`和`provides`。  例如，自定义指令处理器可能接受从用户处打开的文件名称和读取该文件，并且然后将该文件的文本存储在变量名为`fileText`。 一个子类<xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>类可能的值作为用户需要的文件名称`requires`参数，并且要在其中存储的值作为文本变量的名称`provides`参数。 此处理器将打开，读取文件，然后将该文件的文本存储在指定的变量。  
  
 从文本模板中调用自定义指令处理器之前[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，您必须注册它。  
  
 有关如何添加注册表项的详细信息，请参阅[部署自定义指令处理器](../modeling/deploying-a-custom-directive-processor.md)。  
  
## <a name="custom-directives"></a>自定义指令  
 自定义指令类似如下所示：  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`  
  
 当你想要从文本模板访问外部数据或资源时，你可以使用自定义指令处理器。  
  
 不同的文本模板可以共享单个指令处理器提供的功能，因此指令处理器提供因素代码的方法，以供重复使用。 内置`include`指令非常相似，因为你可以使用它来抽取代码，在不同的文本模板之间进行共享。 区别在于任何功能，`include`指令提供了固定的不接受参数。 如果你想要提供到文本模板的常见功能，并允许要将参数传递的模板，则必须创建自定义指令处理器。  
  
 可能是自定义指令处理器的一些示例：  
  
-   用于从作为参数接受用户名和密码的数据库中返回数据的指令处理器。  
  
-   指令处理器来打开和读取文件作为参数接受的文件的名称。  
  
### <a name="principal-parts-of-a-custom-directive-processor"></a>自定义指令处理器的主体部分  
 若要开发指令处理器，你必须创建继承自类<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>或<xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>。  
  
 最重要`DirectiveProcessor`必须实现的方法如下所示。  
  
-   `bool IsDirectiveSupported(string directiveName)`-返回`true`如果指令处理器可以处理命名指令。  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)`-模板引擎在每个出现的模板中的指令调用此方法。 你的处理器应保存结果。  
  
 在对 ProcessDirective() 的所有调用之后模板化引擎将调用这些方法：  
  
-   `string[] GetReferencesForProcessingRun()`-返回的模板代码需要的程序集的名称。  
  
-   `string[] GetImportsForProcessingRun()`-返回可使用的命名空间中的模板代码。  
  
-   `string GetClassCodeForProcessingRun()`-返回代码的方法、 属性和模板代码可使用其他声明。 若要执行此操作的最简单方法是生成包含 C# 或 Visual Basic 代码的字符串。 若要使能够从使用任何 CLR 语言的模板调用指令处理器，可以构造 CodeDom 目录树形式的语句，然后返回结果的序列化的树中使用模板的语言。  
  
-   有关详细信息，请参阅[演练： 创建自定义指令处理器](../modeling/walkthrough-creating-a-custom-directive-processor.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [部署自定义指令处理器](../modeling/deploying-a-custom-directive-processor.md)  
 介绍了如何注册自定义指令处理器。  
  
 [演练：创建自定义指令处理器](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 描述如何创建自定义指令处理器，如何注册和测试指令处理器，以及如何将输出文件格式化为 HTML。
