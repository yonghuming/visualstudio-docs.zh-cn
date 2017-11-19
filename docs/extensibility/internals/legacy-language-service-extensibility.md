---
title: "旧语言服务可扩展性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: "42"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5072aef90e08d645bff2a1bb6800e409e7d2104
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-extensibility"></a>旧语言服务可扩展性
语言服务用于编辑在 IDE 中的源代码提供特定于语言的支持。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解有关实现语言服务的新方式的详细信息，请参阅[编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
 本部分讨论的结构和旧语言服务实现。  
  
## <a name="in-this-section"></a>本节内容  
 [迁移旧版语言服务](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 说明如何更新语言服务从 Visual Studio 2008 的最新版本。  
  
 [旧版语言服务基础知识](../../extensibility/internals/legacy-language-service-essentials.md)  
 提供有关如何开发语言服务集成到 Visual Studio 中，一种编程语言的重要信息。  
  
 [开发旧版语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)  
 提供可帮助你创建语言服务主题的链接。  
  
 [在旧版语言服务中进行语法着色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 提供有关支持语法突出显示语言服务中的信息。  
  
 [实现旧语言服务](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 提供有关如何使用托管的包框架 (MPF) 在托管代码中实现齐全语言服务的信息。  
  
 [支持符号浏览工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 描述库和工具，可帮助你浏览的符号在 IDE 中的树视图。  
  
## <a name="related-sections"></a>相关章节  
 [编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)  
 概述 Visual Studio 编辑器。  
  
 [用于调试的语言服务支持](../../extensibility/internals/language-service-support-for-debugging.md)  
 提供有关信息和链接到 Visual Studio 调试 SDK，其中包含需要创建和自定义使用调试程序的调试器组件的信息。