---
title: "自动格式设置在传统语言服务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "语言服务，自动格式设置"
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 自动格式设置在传统语言服务
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

自动套用格式，自动语言服务插入代码段，当用户开始键入已知的代码构造。  
  
## 自动格式设置行为  
 例如，那么，当您自动键入 `if`，与大括号时的语言服务插入，或者，如果您按 enter 键，语言服务在新行强制插入点移到适当的缩进级别，按照上面的行是否打开新范围。  
  
 用于语言服务的其余部分的命令筛选器可以为自动格式设置也使用。  通过调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>还显示了匹配的大括号。  
  
## 请参阅  
 [开发语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)