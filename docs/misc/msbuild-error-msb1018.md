---
title: "MSBuild 错误 MSB1018 | Microsoft Docs"
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
  - "MSBuild.InvalidVerbosityError"
helpviewer_keywords: 
  - "MSB1018"
ms.assetid: fb4deacc-a799-44e8-8980-d70d9da4caa1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB1018
**详细级别无效。**  
  
 指定的详细级别不是其中一个可用的详细级别。  
  
### 更正此错误  
  
1.  检查详细级别的拼写是否正确。  可用的详细级别有：q\[uiet\]、m\[inimal\]、n\[ormal\]、d\[etailed\] 和 diag\[nostic\]，例如，`/verbosity:quiet`、 `/verbosity:q` 或 `/v:q`  
  
## 请参阅  
 [命令行参考](../msbuild/msbuild-command-line-reference.md)   
 [生成记录器](../msbuild/build-loggers.md)