---
title: "MSBuild 错误 MSB1002 | Microsoft Docs"
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
  - "MSBuild.UnexpectedParametersError"
helpviewer_keywords: 
  - "MSB1002"
ms.assetid: 798c9690-6d99-4f21-a491-ab44d3f3c552
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB1002
**此开关不接受任何参数。**  
  
 不能定义此开关的参数。  只需要此开关的名称，而且名称后面不能有冒号。  
  
### 更正此错误  
  
-   键入此开关的不带参数的命令，即键入 `msbuild /<switch>`，而不是键入 `msbuild /<switch>:<parameters>`。  
  
-   删除开关名称后面的冒号，即键入 `msbuild /<switch>`，而不是键入 `msbuild /<switch>:`。  
  
## 请参阅  
 [命令行参考](../msbuild/msbuild-command-line-reference.md)