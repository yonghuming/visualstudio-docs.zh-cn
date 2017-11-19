---
title: "实现旧语言 Service1 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18ff0fef277967dcb446f62120843f476ddb4a3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-a-legacy-language-service"></a>实现旧语言服务
你可以使用托管的包框架 (MPF) 中的类来实现旧语言服务支持各种功能，如语法突出显示、 大括号匹配和 IntelliSense 完成。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解有关实现语言服务的新方式的详细信息，请参阅[编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="in-this-section"></a>本节内容  
 [旧版语言服务概述](../../extensibility/internals/legacy-language-service-overview.md)  
 MPF 中支持的语言服务功能的概述。  
  
 [实现旧语言服务](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 描述什么是需要通过使用 MPF 实现语言服务。  
  
 [注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 介绍注册具有的 MPF 基于语言服务所需的步骤[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [旧版语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 介绍通过使用 MPF 实现的语言服务的所有功能所需的两个分析器。  
  
 [演练：创建旧版语言服务](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 提供在 VSPackage 中实现的 MPF 语言服务所需的基本步骤。  
  
 [演练：获取安装代码片段（旧版实现）的列表](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 演示安装的代码代码段的列表中检索的技术。  
  
 [旧语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)  
 提供的主题链接，必须执行哪些使用 MPF 实现的语言服务的所有功能的详细信息。