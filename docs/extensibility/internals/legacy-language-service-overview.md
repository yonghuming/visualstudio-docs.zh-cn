---
title: "旧语言服务概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d586851da7d02f89335a3920364e25b7f4876860
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-overview"></a>旧语言服务概述
语言服务提供了编辑器支持，使您可以实现某些[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]功能。 托管包框架 (MPF) 语言服务类提供完全支持常用的功能以及对其他功能的部分支持。  
  
## <a name="fully-supported-features-in-the-mpf"></a>MPF 中完全支持的功能  
 MPF 语言服务类支持以下功能：  
  
-   语法突出显示  
  
-   大纲显示  
  
-   注释的代码块  
  
-   大括号匹配  
  
-   代码片段  
  
-   自定义文档属性  
  
-   IntelliSense 参数信息  
  
-   IntelliSense 快速信息  
  
-   IntelliSense 成员完成  
  
-   IntelliSense 单词完成  
  
## <a name="partially-supported-features-in-the-mpf"></a>MPF 中部分支持的功能  
 MPF 提供以下功能只进行了部分支持。 这意味着你必须实现由 MPF 调用的方法。  
  
-   重新格式化代码。 提供用于实现重新格式化的代码。  
  
-   验证通过标识有效的代码的断点跨越。 你提供代码标识的代码范围。  
  
-   支持调试器**自动**窗口用于显示变量。 提供确定如何在窗口中显示的代码。  
  
-   支持**导航栏**类型和成员之间快速导航。 实现并返回填充的列表中的帮助器类**导航栏**组合框。  
  
## <a name="implementation"></a>实现  
 你必须完成几个步骤来实现语言服务本身和你想要为您的语言支持的语言服务功能。 以下主题中讨论了这些步骤：  
  
-   [实现旧语言服务](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [旧版语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [旧版语言服务中的大括号匹配](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [旧版语言服务中的大纲显示](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [在旧版语言服务中注释代码](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [在旧版语言服务中重新格式化代码](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [在旧版语言服务中自定义文档属性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [旧版语言服务中的代码片段支持](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [旧版语言服务中的导航栏支持](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [旧版语言服务中的文字完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [旧版语言服务中的成员完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [参数信息，请参阅旧语言服务](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [旧版语言服务中的快速信息](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [旧版语言服务中的自动窗口支持](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [验证旧版语言服务中的断点](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>另请参阅  
 [实现旧语言服务](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [旧版语言服务扩展性](../../extensibility/internals/legacy-language-service-extensibility.md)