---
title: "文本模板的安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文本模板, 安全性"
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 23
---
# 文本模板的安全性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文本模板具有以下安全问题：  
  
-   文本模板容易受到任意代码插入的攻击。  
  
-   如果宿主用于查找指令处理器的机制不安全，则可能会运行恶意指令处理器。  
  
## 任意代码  
 编写模板时，可在 \<\# \#\> 标记中放置任何代码。  此操作会允许任意代码从文本模板内部执行。  
  
 请务必从受信任的来源获取模板。  请确保警告应用程序的最终用户不要执行不是来自受信任来源的模板。  
  
## 恶意指令处理器  
 文本模板引擎可与转换宿主以及一个或多个指令处理器进行交互，以将模板文本转换为输出文件。  有关更多信息，请参见[文本模板转换过程](../modeling/the-text-template-transformation-process.md)。  
  
 如果宿主用于查找指令处理器的机制不安全，则会面临运行恶意指令处理器的风险。  运行模板时，恶意指令处理器可提供以 `FullTrust` 模式运行的代码。  如果创建自定义文本模板转换宿主，则必须使用安全机制（如注册表），以便引擎定位指令处理器。