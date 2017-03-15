---
title: "遗留语言服务可扩展性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "语言服务"
  - "Visual Studio 中，语言服务"
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 42
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 42
---
# 遗留语言服务可扩展性
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

语言服务提供用于编辑源代码，在 IDE 中的特定于语言的支持。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要了解有关实现语言服务的新方法的详细信息，请参阅 [编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
 本部分讨论的结构和遗留语言服务实现。  
  
## 本节内容  
 [迁移早期语言服务](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 介绍如何更新到最新版本从 Visual Studio 2008 语言服务。  
  
 [遗留语言服务基础知识](../../extensibility/internals/legacy-language-service-essentials.md)  
 提供有关如何开发语言服务，以集成到 Visual Studio 的一种编程语言的重要信息。  
  
 [开发语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)  
 提供可帮助您创建语言服务的主题的链接。  
  
 [语法着色在传统语言服务](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 提供有关支持的语言服务中语法突出显示的信息。  
  
 [实现传统语言服务](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 提供有关如何使用托管的包框架 \(MPF\) 以在托管代码中实现完备的语言服务的信息。  
  
 [支持符号浏览工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 介绍库和工具，您可以浏览在 IDE 中的符号的树视图。  
  
## 相关章节  
 [编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)  
 概述 Visual Studio 编辑器。  
  
 [语言服务支持以进行调试](../../extensibility/internals/language-service-support-for-debugging.md)  
 提供有关的信息以及链接到 Visual Studio Debugging SDK，其中包含是创建和自定义调试器组件用来调试程序所必需的信息。