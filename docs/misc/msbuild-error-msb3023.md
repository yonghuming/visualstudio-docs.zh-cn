---
title: "MSBuild 错误 MSB3023 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Copy.NeedsDestination"
helpviewer_keywords: 
  - "MSB3023"
ms.assetid: 3505ad1e-d54f-4cb4-a299-ac03684cb391
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3023
**未指定复制目标。  请提供“\<特性\>”或“\<特性\>”。**  
  
 必须使用任务特性 `DestinationFiles` 和 `DestinationDirectory` 中的一个来指定 `Copy` 任务的目标。  
  
### 更正此错误  
  
-   为 `Copy` 任务指定 `DestinationFiles` 或 `DestinationDirectory`。  
  
## 请参阅  
 [Copy 任务](../msbuild/copy-task.md)   
 [任务](../msbuild/msbuild-tasks.md)