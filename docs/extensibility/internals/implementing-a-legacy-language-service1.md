---
title: "实现传统语言服务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "管理语言服务"
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 实现传统语言服务
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以使用托管的包框架 \(MPF\) 中的类来实现遗留语言服务支持各种功能，如语法突出显示、 大括号匹配和 IntelliSense 完成。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要了解有关实现语言服务的新方法的详细信息，请参阅 [编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
## 本节内容  
 [旧的语言服务概述](../../extensibility/internals/legacy-language-service-overview.md)  
 在 MPF 中支持的语言服务功能概述。  
  
 [实现语言服务](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 描述什么是需要使用 MPF 实现语言服务。  
  
 [注册语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 介绍注册与一种 MPF 基于语言的服务所需的步骤 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [旧的语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 描述两个使用 MPF 实现的语言服务的所有功能所需的分析器。  
  
 [演练︰ 创建传统语言服务](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 提供在 VSPackage 中实现 MPF 语言服务所需的基本步骤。  
  
 [演练︰ 获取安装的代码段 （旧实现） 的列表](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 说明了安装的代码段的列表中检索的方法。  
  
 [遗留语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)  
 提供指向的主题详细描述必须完成什么使用 MPF 实现的语言服务的所有功能。