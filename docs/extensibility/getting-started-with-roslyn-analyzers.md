---
title: "Getting Started with Roslyn 分析器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 962023733d2d746e0acb584e3dcbdc1a5e369012
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-roslyn-analyzers"></a>Getting Started with Roslyn 分析器
使用 Visual Studio 中的实时、 可基于项目的代码分析器，API 作者可以作为其 NuGet 包的一部分提供特定于域的代码分析。  因为这些分析器由.NET Compiler Platform (代码名为"Roslyn") 提供支持，它们可能会产生警告在代码中的，键入甚至之前已完成的行 （没有更多等待生成你的代码以发现问题）。  分析器还外围通过让你立即清理你的代码的 Visual Studio 电灯泡提示自动代码修复  
  
## <a name="getting-started"></a>入门  
 [Roslyn 实时代码分析器简介和演练](https://msdn.microsoft.com/en-us/magazine/dn879356.aspx)  
  
 [添加的代码修复演练： 为分析器的问题提供用户修补程序](https://msdn.microsoft.com/en-us/magazine/dn904670.aspx)  
  
 [简介和实际分析器 Talk 演练](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [真实世界 Roslyn 分析器](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)，你也可以观看作为[对话](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [在 github 上，几个示例分为三种类型的分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
  
 [简介和教程几分析器通信](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)  
  
## <a name="other-resources"></a>其他资源  
 [在 github OSS 站点上的多个文档](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)  
  
 [FxCop 规则实现与 github 上的 Roslyn 分析器](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)