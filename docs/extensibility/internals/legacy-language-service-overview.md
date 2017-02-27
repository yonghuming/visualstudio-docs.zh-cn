---
title: "旧的语言服务概述 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "有关语言服务的语言服务 [托管的包框架]"
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 旧的语言服务概述
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

语言服务提供使您可以实现某些 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 功能的编辑器支持。  托管包 framework \(MPF\) 语言服务类提供对常用的功能完全支持，并且节为任何其他功能的支持。  
  
## 在 MPF 的完全支持的功能  
 MPF 语言服务类支持下列功能:  
  
-   语法突出显示  
  
-   大纲显示  
  
-   注释代码块  
  
-   括号匹配  
  
-   代码段  
  
-   自定义文档属性  
  
-   IntelliSense 参数信息  
  
-   IntelliSense 快速信息  
  
-   IntelliSense 成员完成  
  
-   IntelliSense 文字完成  
  
## 在 MPF 的部分受支持的功能  
 MPF 仅提供部分提供了以下功能的支持。  这意味着您必须执行由 MPF 调用的方法。  
  
-   重新设置代码。  为实现重新设置格式的代码。  
  
-   验证断点通过标识有效的代码范围。  为标识代码大小的代码。  
  
-   支持显示的变量调试器 **汽车** 窗口。  为在窗口中确定如何显示的代码。  
  
-   支持快速导航的 **导航栏** 在类型和成员之间。  您实现并返回该 **导航栏** 组合框列表中的帮助器类。  
  
## 实现  
 您必须执行若干个步骤实现要为该语言支持的语言服务和语言服务功能。  这些步骤。以下主题讨论:  
  
-   [实现语言服务](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [注册语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [在早期语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [传统语言服务中的括号匹配](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [传统语言服务中的大纲显示](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [旧语言服务中的注释代码](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [重新格式化旧语言服务中的代码](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [在早期语言服务中的自定义文档属性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [对旧语言服务中的代码段的支持](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [对旧语言服务中的导航栏的支持](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [在早期语言服务中的单词自动完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [在早期语言服务中的成员完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [传统语言服务中的参数信息](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [在早期语言服务中的快速信息](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [对旧语言服务中的自动窗口的支持](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [验证旧语言服务中的断点](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## 请参阅  
 [实现传统语言服务](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [遗留语言服务可扩展性](../../extensibility/internals/legacy-language-service-extensibility.md)