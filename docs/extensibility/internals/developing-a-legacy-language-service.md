---
title: "开发旧语言服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords: language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e05fb3f0a33c0f033733c40b17d636243c18ee22
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="developing-a-legacy-language-service"></a>开发旧语言服务
此部分链接到主题可帮助您创建旧语言服务。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解有关实现语言服务的新方式的详细信息，请参阅[编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="in-this-section"></a>本节内容  
 [旧版语言服务模型](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 提供的最小语言服务模型[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]核心编辑器。 用于创建你自己的语言服务，可以作为指南使用此模型。  
  
 [旧版语言服务接口](../../extensibility/internals/legacy-language-service-interfaces.md)  
 讨论实现语言服务所需的对象，并提供可用于提供语法突出显示、 方法数据和其他功能的其他对象的列表。  
  
 [截获旧版语言服务命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 描述如何将否则处理文本视图的截距命令到你语言服务中插入命令筛选器。  
  
 [注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 提供有关如何通过使用注册你的语言服务信息[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [用于调试的语言服务支持](../../extensibility/internals/language-service-support-for-debugging.md)  
 描述如何语言服务可以提供功能以支持调试器。  
  
 [清单：创建旧版语言服务](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 提供有关创建和集成核心编辑器语言服务的分步说明。  
  
## <a name="related-sections"></a>相关章节  
 [在旧版语言服务中进行语法着色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 讨论如何实现语法突出显示语言服务中。  
  
 [旧版语言服务中的语句完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 讨论语句完成、 依据语言服务可帮助用户完成语言关键字或它们已启动键入的元素的过程。  
  
 [参数信息，请参阅旧语言服务](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 描述如何为重载的函数和方法提供方法提示。  
  
 [如何：提供旧版语言服务中的隐藏文本](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 说明用途的隐藏的文本区域，并提供有关如何实现一个隐藏的文本区域的说明。  
  
 [如何：提供旧版语言服务中扩展的大纲显示支持](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 说明了扩展对你仅仅是支持的语言的大纲显示支持的两个选项*折叠到定义*命令。