---
title: "旧语言服务 Essentials |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 577010320dc4aa0a726e7c0befba8173245681e7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-essentials"></a>旧语言服务 Essentials
必须提供语言服务将一种编程语言集成到 Visual Studio。 本主题介绍旧语言服务中提供的功能。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解有关实现语言服务的新方式的详细信息，请参阅[编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
 旧语言服务提供以下功能：  
  
|功能|描述|  
|-------------|-----------------|  
|语法着色|使编辑器视图以显示不同颜色和一种语言的不同元素的字体样式。 此差异使其更容易阅读和编辑文件。<br /><br /> 有关常规信息，请参阅[语法突出显示在旧语言服务](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。<br /><br /> 有关此功能的托管的包框架 (MPF) 的信息，请参阅[旧语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。|  
|语句结束|完成的语句或用户已开始键入的关键字。 语句结束有助于用户键入与错误的更少概率更轻松地输入困难的语句。<br /><br /> 有关常规信息，请参阅[旧语言服务中的语句结束](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。<br /><br /> MPF 中此功能的信息，请参阅[旧语言服务中的单词完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)。|  
|大括号匹配|如大括号突出显示了配对的字符。 当用户键入结束字符如"}"，大括号匹配突出显示相应的开始字符，如"{"。 当存在多个级别的封闭字符时，此功能可帮助用户确认正确配对的封闭字符。<br /><br /> MPF 中此功能的信息，请参阅[旧语言服务中的大括号匹配](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)。|  
|参数信息工具提示|显示当前键入用户的重载方法可能签名中的列表。<br /><br /> 有关常规信息，请参阅[参数信息，请参阅旧语言服务](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。<br /><br /> MPF 中此功能的信息，请参阅[参数信息，请参阅旧语言服务](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)。|  
|错误标记|显示红色波浪下划线，也称为波浪下的语法不正确的文本。 错误标记通常用于使用户能够识别拼错的关键字、 闭合的括号、 无效的字符，以及类似的错误。<br /><br /> 在 MPF 类中，自动在处理错误标记<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>方法<xref:Microsoft.VisualStudio.Package.AuthoringSink>类。|  
  
 其中的许多功能都需要语言服务将源代码分析。 通常，你可以重用将拆分为标记和分析你的编译器或解释程序代码。  
  
 以下功能与相关的其他编程语言支持，但不是语言服务的一部分：  
  
|功能|描述|  
|-------------|-----------------|  
|表达式计算器|支持[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通过验证断点并提供的表达式列表的调试器中显示**自动**调试窗口。<br /><br /> 有关详细信息，请参阅[以便进行调试的语言服务支持](../../extensibility/internals/language-service-support-for-debugging.md)。|  
|符号浏览工具|支持**对象浏览器**，**类视图**，**调用浏览器**，和**查找符号结果**。|