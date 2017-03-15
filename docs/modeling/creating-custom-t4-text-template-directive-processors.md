---
title: "创建自定义 T4 文本模板指令处理器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文本模板, 自定义指令处理器"
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# 创建自定义 T4 文本模板指令处理器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文本模板转换过程将文本模板文件作为输入，并生成一个文本文件作为输出。  文本模板转换引擎控制该过程，该引擎与文本模板转换宿主以及一个或多个文本模板指令处理器进行交互，以完成该过程。  有关更多信息，请参见[文本模板转换过程](../modeling/the-text-template-transformation-process.md)。  
  
 若要创建自定义指令处理器，需要创建一个从 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 继承的类。  
  
 这两者之间的区别在于 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 实现从用户处获取参数以及生成产生模板输出文件的代码所需的最小接口。  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 实现要求\/提供设计模式。  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 处理两个特殊参数 `requires` 和 `provides`。  例如，某个自定义指令处理器可能会从用户处接受文件名，打开并读取该文件，然后将该文件的文本存储在名为 `fileText` 的变量中。  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 类的子类可能会采用来自用户的文件名作为 `requires` 参数的值，并采用存储文本的变量的名称作为 `provides` 参数的值。  此处理器会打开并读取文件，然后将文件的文本存储在指定变量中。  
  
 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中从文本模板调用自定义指令处理器之前，必须先注册该处理器。  
  
 有关如何添加注册表项的更多信息，请参见[部署自定义指令处理器](../modeling/deploying-a-custom-directive-processor.md)。  
  
## 自定义指令  
 自定义指令类似于下面这样：  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`  
  
 在要从文本模板访问外部数据或资源时，可以使用自定义指令处理器。  
  
 不同的文本模板可共享一个指令处理器提供的功能，因此指令处理器提供了一种方式来分解代码以便重用。  内置 `include` 指令是类似的，因为您可以使用该指令分解代码，并在不同的文本模板之间进行共享。  不同之处在于，`include` 指令提供的任何功能都是固定的，不接受参数。  如果要为文本模板提供通用功能，并允许模板传递参数，则必须创建自定义指令处理器。  
  
 自定义指令处理器的一些示例可能包括：  
  
-   接受用户名和密码作为参数从数据库返回数据的指令处理器。  
  
-   接受文件名作为参数打开和读取文件的指令处理器。  
  
### 自定义指令处理器的主要部件  
 若要开发指令处理器，必须创建一个从 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 继承的类。  
  
 必须实现的最重要的 `DirectiveProcessor` 方法如下。  
  
-   `bool IsDirectiveSupported(string directiveName)` \- 如果指令处理器可以处理命名指令，则返回 `true`。  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` \- 模板引擎会为指令在模板中的每次出现调用此方法。  处理器应保存结果。  
  
 在对 ProcessDirective\(\) 的所有调用之后，模板化引擎会调用以下这些方法：  
  
-   `string[] GetReferencesForProcessingRun()` \- 返回模板代码需要的程序集的名称。  
  
-   `string[] GetImportsForProcessingRun()` \- 返回可在模板代码中使用的命名空间。  
  
-   `string GetClassCodeForProcessingRun()` \- 返回模板代码可以使用的方法、属性和其他声明的代码。  实现此目的的最简单方法是生成包含 C\# 或 Visual Basic 代码的字符串。  若要能够从使用任何 CLR 语言的模板调用指令处理器，可以将语句构造为 CodeDom 树，然后返回采用模板使用的语言对树进行序列化的结果。  
  
-   有关更多信息，请参见[演练：创建自定义指令处理器](../modeling/walkthrough-creating-a-custom-directive-processor.md)。  
  
## 本节内容  
 [部署自定义指令处理器](../modeling/deploying-a-custom-directive-processor.md)  
 说明如何注册自定义指令处理器。  
  
 [演练：创建自定义指令处理器](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 描述如何创建自定义指令处理器、如何注册和测试指令处理器以及如何将输出文件格式化为 HTML。