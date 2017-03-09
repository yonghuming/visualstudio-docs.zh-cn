---
title: "MSBuild 错误 MSB1012 | Microsoft Docs"
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
  - "MSBuild.MissingResponseFileError"
helpviewer_keywords: 
  - "MSB1012"
ms.assetid: 6e09e21d-9f64-4a8c-adec-f8efb28b7ac2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB1012
**指定响应文件。**  
  
 必须为 @ 开关指定响应文件。  
  
### 更正此错误  
  
-   指定响应文件。  语法是 @\<file name\>，例如 `@BuildHW.txt` 。  
  
-   不要在命令行中包括 @ 开关。  
  
## 请参阅  
 [命令行参考](../msbuild/msbuild-command-line-reference.md)