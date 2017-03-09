---
title: "MSBuild 错误 MSB1016 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.MissingVerbosityError"
helpviewer_keywords: 
  - "MSB1016"
ms.assetid: 967a9757-0513-48ae-bf1d-b1b019993c70
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB1016
**指定详细级别。**  
  
 必须指定 **\/verbosity** 开关的详细级别。  
  
### 更正此错误  
  
1.  使用格式 `/verbosity:<level>` 指定详细级别。  可用的详细级别有：q\[uiet\]、m\[inimal\]、n\[ormal\]、d\[etailed\] 和 diag\[nostic\]，例如，`/verbosity:quiet`、 `/verbosity:q` 或 `/v:q`  
  
## 请参阅  
 [命令行参考](../msbuild/msbuild-command-line-reference.md)