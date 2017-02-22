---
title: "使用自定义宿主处理文本模板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文本模板, 自定义指令宿主"
  - "文本模板, 在应用程序或 VS 扩展中"
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 33
caps.handback.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 使用自定义宿主处理文本模板
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文本模板转换过程将文本模板文件作为输入，并生成一个文本文件作为输出。  从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 扩展或安装有 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的计算机上运行的独立应用程序，可以调用文本转换引擎。  不过，您必须提供文本模板化宿主。  该类将模板连接到环境，查找资源（如程序集和包含文件），并处理输出和错误消息。  
  
> [!TIP]
>  如果要编写将在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内运行的包或扩展，请考虑使用文本模板化服务而不是编写您自己的主机。  有关更多信息，请参见[在 VS 扩展中调用文本转换](../modeling/invoking-text-transformation-in-a-vs-extension.md)。  
  
> [!NOTE]
>  不建议在服务器应用程序中使用文本模板转换。  除非是在单个线程中，否则不建议使用文本模板转换。  这是因为文本模板化引擎可以重用单个 AppDomain，以便转换、编译和执行模板。  转换的代码未被设计为线程安全的。  该引擎旨在按顺序处理文件，因为在设计时它们位于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目中。  
>   
>  对于运行时应用程序，请考虑使用预处理过的文本模板：请参见[使用 T4 文本模板的运行时文本生成](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
 如果应用程序使用一组在编译时固定的模板，使用预处理文本模板会更为简单。  如果应用程序将在未安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的计算机上运行，也可以使用该方法。  有关更多信息，请参见[使用 T4 文本模板的运行时文本生成](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
## 在应用程序中执行文本模板  
 若要执行文本模板，可以调用 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> 的 ProcessTemplate 方法。  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 应用程序必须找到并提供模板，并且必须处理输出。  
  
 在 `host` 参数中，必须提供实现 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> 的类。  这是由引擎回调的。  
  
 宿主必须能记录错误、解析对程序集和包含文件的引用、提供可在其中执行模板的应用程序域并为每条指令调用相应的处理器。  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> 在 **Microsoft.VisualStudio.TextTemplating.\*.0.dll** 中定义，<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> 在 **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0.dll** 中定义。  
  
## 本节内容  
 [演练：创建自定义文本模板宿主](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 演示如何创建自定义文本模板宿主，从而使文本模板功能在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 外可用。  
  
## 参考  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## 相关章节  
 [文本模板转换过程](../modeling/the-text-template-transformation-process.md)  
 说明文本转换的工作原理以及可以自定义的部分。  
  
 [创建自定义 T4 文本模板指令处理器](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 提供文本模板指令处理器的概述。