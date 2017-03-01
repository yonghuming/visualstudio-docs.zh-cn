---
title: "遗留语言服务 Features2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
caps.latest.revision: 16
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
ms.openlocfilehash: 93bbf3ce9f8252254d1ca589761c4d7c2b01d9b4
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-language-service-features"></a>遗留语言服务功能
以下主题列出了一些你可以提供遗留语言服务功能。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要了解有关实现语言服务的新方法的详细信息，请参阅[编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="in-this-section"></a>本节内容  
 [语法着色在传统语言服务](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 介绍如何实现︰ 语法着色。  
  
 [自动格式设置在传统语言服务](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)  
 说明如何实现自动格式设置。  
  
 [传统语言服务中的参数信息](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 介绍如何实现 IntelliSense 参数信息工具提示。  
  
 [传统语言服务中的语句结束](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 介绍如何实现 IntelliSense 语句列表和成员完成列表。  
  
 [在早期语言服务中的大纲显示和隐藏文本](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)  
 说明如何实现的大纲显示或隐藏的文本。  
  
 [如何︰ 提供旧语言服务中的扩展大纲显示支持](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 介绍一些实现调试器支持中的步骤...  
  
## <a name="related-sections"></a>相关章节
