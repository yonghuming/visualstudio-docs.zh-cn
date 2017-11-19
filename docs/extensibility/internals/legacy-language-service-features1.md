---
title: "旧语言服务 Features1 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc29529c7ba499cdc7291078774b9f546a3a08ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-features"></a>旧语言服务功能
托管的包框架 (MPF) 语言服务可以支持一个或多[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]功能，如语法突出显示、 IntelliSense、 和断点验证。 每个功能可以实现独立于其他但所有需要的分析程序和除外语法突出显示，这需要仅扫描程序扫描程序。  
  
## <a name="in-this-section"></a>本节内容  
 [旧版语言服务中的大括号匹配](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 描述什么是需要以支持语言对匹配，也称为大括号匹配。  
  
 [在旧版语言服务中注释代码](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 描述的要求来支持进行注释和取消的所选代码的注释。  
  
 [在旧版语言服务中自定义文档属性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 描述的要求来支持在源文件中嵌入的文档属性。  
  
 [旧版语言服务中的大纲显示](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 描述的要求来支持大纲显示通过的隐藏区域的实现。  
  
 [在旧版语言服务中重新格式化代码](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 描述的要求来支持重新格式化代码。  
  
 [旧版语言服务中的代码片段支持](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 描述的要求来支持代码段，它们是代码段的插入，可以进行编辑。  
  
 [参数信息，请参阅旧语言服务](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 描述的要求来支持类型化方法时，显示的方法签名的 IntelliSense 参数信息操作。  
  
 [旧版语言服务中的快速信息](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 描述的要求来支持用于显示有关标识符的信息的 IntelliSense 快速信息操作。  
  
 [旧版语言服务中的成员完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 描述什么支持从列表中选择一个命名空间的成员的 IntelliSense 成员完成操作所必需。  
  
 [旧版语言服务中的文字完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 描述的要求来支持用于完成部分类型化的单词的智能感知完成单词操作。  
  
 [旧版语言服务中的自动窗口支持](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 描述什么语言服务如何支持**自动**窗口进行调试时。  
  
 [旧版语言服务中的导航栏支持](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 介绍如何使用**导航栏**顶部提供快速导航到任何类型或成员在该视图中显示文件中的编辑器视图...  
  
 [旧版语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 描述的要求来支持语法突出显示代码的源代码。  
  
 [验证旧版语言服务中的断点](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 介绍语言服务可以执行的工作以支持调试器外部验证断点。  
  
## <a name="related-sections"></a>相关章节  
 [旧版语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 描述的分析器和扫描程序所需实现使用托管的包框架的语言服务的所有功能。  
  
 [实现旧语言服务](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 描述什么是需要通过使用 MPF 实现语言服务。  
  
 [注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 介绍注册具有的 MPF 基于语言服务所需的步骤[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [使用 IntelliSense](../../ide/using-intellisense.md)  
 说明如何使用 IntelliSense 可以语言引用可以轻松地访问。  
  
 [实现旧语言服务](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 提供有关如何使用托管的包框架 (MPF) 在托管代码中实现齐全语言服务的信息。