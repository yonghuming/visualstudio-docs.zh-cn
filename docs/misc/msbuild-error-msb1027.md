---
title: "MSBuild 错误 MSB1027 | Microsoft Docs"
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
  - "MSBuild.CannotAutoDisableAutoResponseFile"
helpviewer_keywords: 
  - "MSB1027"
ms.assetid: 2ef8d643-616c-4608-be76-5c2c8e18a9e7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB1027
**不能在 MSBuild.rsp 自动响应文件中指定 \/noautoresponse 开关，也不能在该自动响应文件引用的任何响应文件中指定该开关。**  
  
 在 MSBuild.rsp 文件中或 MSBuild.rsp 文件包括的另一个响应文件中发现 **\/noautoresponse** 开关。  不可将自动响应文件用于关闭自身。  
  
### 更正此错误  
  
-   指定不同的响应文件  
  
-   从 MSBuild.rsp 响应文件中移除 **\/noautoresponse** 开关。  
  
## 请参阅  
 [命令行参考](../msbuild/msbuild-command-line-reference.md)