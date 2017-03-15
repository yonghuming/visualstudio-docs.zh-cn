---
title: "通过 Roslyn 分析器入门 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4a71add3ac837e3727d54b379b6e82ee126e4a3f
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-roslyn-analyzers"></a>开始使用 Roslyn 分析器
通过 Visual Studio 中的实时、 基于项目的代码分析器，API 作者可以提供特定于域的代码分析作为其 NuGet 程序包的一部分。  由于这些分析器由.NET 编译器平台 (代号为"Roslyn") 提供支持，它们可能会产生在代码中的警告，当您键入甚至之前已完成 （不再等到生成代码时才发现的问题） 的行。  分析器可能也显示通过 Visual Studio 灯泡图标提示来让您立即清理代码自动代码修补程序  
  
## <a name="getting-started"></a>入门  
 [Roslyn 实时代码分析器简介和演练](https://msdn.microsoft.com/en-us/magazine/dn879356.aspx)  
  
 [添加代码修复演练︰ 分析工具问题提供用户修补程序](https://msdn.microsoft.com/en-us/magazine/dn904670.aspx)  
  
 [简介和演练的现实世界分析器讨论](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [真实世界的 Roslyn 分析器](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)，你也可以观看作为[对话](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [在 github 上，几个示例分为三种类型的分析工具](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
  
 [简介和几个分析器教程讨论](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)  
  
## <a name="other-resources"></a>其他资源  
 [Github OSS 网站上的多个文档](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)  
  
 [通过在 github 上的 Roslyn 分析器实现的 FxCop 规则](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
