---
title: "遗留语言服务 Features1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "语言服务 [托管的包框架]"
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 遗留语言服务功能
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

托管包 framework \(MPF\) 语言服务可支持一个或多 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 功能，比如语法显示， IntelliSense 和验证断点。  每个功能都可以是其他的实现无关，但所有需要一个分析器和一个扫描仪除了显示的语法，只需要一个扫描仪。  
  
## 本节内容  
 [传统语言服务中的括号匹配](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 描述了哪些支持语言来匹配，也称为括号匹配。  
  
 [旧语言服务中的注释代码](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 描述了哪些支持注释和取消注释选定的代码。  
  
 [在早期语言服务中的自定义文档属性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 描述了哪些支持文档在源文件嵌入的属性。  
  
 [传统语言服务中的大纲显示](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 描述要求。通过隐藏区域的实现支持大纲显示。  
  
 [重新格式化旧语言服务中的代码](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 描述了哪些支持重新设置代码。  
  
 [对旧语言服务中的代码段的支持](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 描述了哪些支持代码段，是代码段插入并进行编辑。  
  
 [传统语言服务中的参数信息](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 描述了哪些支持显示方法签名的 IntelliSense 参数信息操作，则方法中键入。  
  
 [在早期语言服务中的快速信息](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 描述了哪些支持显示信息的 IntelliSense 快速信息操作有关标识符。  
  
 [在早期语言服务中的成员完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 描述了哪些支持选择命名空间中的成员的 IntelliSense 成员完成操作从列表。  
  
 [在早期语言服务中的单词自动完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 描述了哪些支持完成部分已键入的单词的 IntelliSense 完成单词操作。  
  
 [对旧语言服务中的自动窗口的支持](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 描述语言服务可以执行支持 **汽车** 窗口中，在调试时。  
  
 [对旧语言服务中的导航栏的支持](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 描述如何使用在编辑视图的顶部之间 **导航栏** 提供比在该视图中显示的文件的导航对任何类型或成员。  
  
 [在早期语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 描述了哪些支持语法显示源代码。  
  
 [验证旧语言服务中的断点](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 描述语言服务可以执行支持验证在调试器外部的断点。  
  
## 相关章节  
 [旧的语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 描述实现语言服务所有函数使用托管包结构的分析器和 scan 程序。  
  
 [实现语言服务](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 介绍需要使用 MPF，实现语言服务。  
  
 [注册语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 描述需要与注册 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的基于 MPF 的语言服务的步骤。  
  
 [使用 IntelliSense](../../ide/using-intellisense.md)  
 解释 IntelliSense 如何使语言参考方便地访问。  
  
 [实现传统语言服务](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 提供有关如何使用托管包结构 \(MPF\)实现托管代码功能齐全的语言服务。