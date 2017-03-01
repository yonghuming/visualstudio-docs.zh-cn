---
title: "遗留语言服务基础知识 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 21
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
ms.openlocfilehash: f6f8ba46289e27b2465436a103091983c17de1c0
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-language-service-essentials"></a>遗留语言服务基础知识
您必须提供要集成到 Visual Studio 的一种编程语言的语言服务。 本主题说明遗留语言服务中提供的功能。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要了解有关实现语言服务的新方法的详细信息，请参阅[编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
 旧的语言服务提供以下功能︰  
  
|功能|描述|  
|-------------|-----------------|  
|语法着色|导致编辑器视图以显示不同的颜色和一种语言的不同元素的字体样式。 此差异可以更加轻松地阅读和编辑文件。<br /><br /> 有关一般信息，请参阅[语法突出显示旧语言服务中](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。<br /><br /> 有关此功能的托管的包框架 (MPF) 的信息，请参阅[旧语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。|  
|语句结束|完成语句或用户已开始键入的关键字。 语句结束有助于减少键入和较少的出错机会更轻松地输入困难语句的用户。<br /><br /> 有关一般信息，请参阅[早期语言服务中的语句完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。<br /><br /> 有关此功能的 MPF 的信息，请参阅[旧语言服务中的单词自动完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)。|  
|大括号匹配|突出显示配对字符，如大括号。 当用户键入结束字符如"}"，大括号匹配突出显示相应的开始字符，如"{"。 当存在多个级别的封闭字符时，此功能可帮助用户确认正确配对的封闭字符。<br /><br /> 有关此功能的 MPF 的信息，请参阅[早期语言服务中的大括号匹配](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)。|  
|参数信息工具提示|显示可能在用户当前正在键入的重载方法签名中的列表。<br /><br /> 有关一般信息，请参阅[早期语言服务中的参数信息](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。<br /><br /> 有关此功能的 MPF 的信息，请参阅[早期语言服务中的参数信息](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)。|  
|错误标记|显示红色的波浪下划线，也称为波浪线，下面的语法不正确的文本。 错误标记通常用于使用户意识到拼错的关键字、 不完整的括号、 无效的字符，以及类似错误。<br /><br /> 在 MPF 类中，错误标记会自动在处理<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>方法的<xref:Microsoft.VisualStudio.Package.AuthoringSink>类。</xref:Microsoft.VisualStudio.Package.AuthoringSink> </xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>|  
  
 其中的许多功能需要分析源代码的语言服务。 通常，您可以重用将拆分为标记和分析代码编译器或解释器。  
  
 下列功能与相关的编程语言的支持，但是不是语言服务的一部分︰  
  
|功能|说明|  
|-------------|-----------------|  
|表达式计算器|支持[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]验证断点并提供一组表达式的调试器中显示**自动**调试窗口。<br /><br /> 有关详细信息，请参阅[以便进行调试的语言服务支持](../../extensibility/internals/language-service-support-for-debugging.md)。|  
|符号浏览工具|支持**对象浏览器**，**类视图**，**调用浏览器**，和**查找符号结果**。|
