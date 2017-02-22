---
title: ".NET 编译器平台 (&quot;Roslyn&quot;) 可扩展性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# .NET 编译器平台 (&quot;Roslyn&quot;) 可扩展性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

.NET Compiler Platform \("Roslyn"\) 的核心任务是开放的 C\# 和 Visual Basic 编译器，允许工具和开发人员能够在丰富的信息的编译器中共享有程序的相关。 代码分析工具提高代码质量和代码生成器帮助在应用程序构造。 随着工具越来越聪明，他们需要访问到越来越多的仅编译器具有深代码知识。 而不是不透明的翻译人员 \(中的源代码和扩展对象代码\)，Roslyn 编译器提供了可用于在您的工具和应用程序中与代码相关的任务的 Api。  
  
 最值得称道之 Roslyn 编译器、 其 Api、 示例和演练中和基于这些 Api 的真正工具是完全开放源码站点 [github.com\/dotnet\/roslyn](https://github.com/dotnet/Roslyn)。 请转到 OSS 网站以了解详细信息和开始使用 Roslyn。 您会发现链接以获取最新 C\# 和 VB 功能，可以使用作为最终用户，以及链接以开始与利用 Roslyn Api 工具生成器。  
  
## 请参阅  
 [开始使用 Roslyn 分析器](../extensibility/getting-started-with-roslyn-analyzers.md)