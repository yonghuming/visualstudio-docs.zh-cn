---
title: "MSBuild 错误 MSB3022 | Microsoft Docs"
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
  - "MSBuild.Copy.ExactlyOneTypeOfDestination"
helpviewer_keywords: 
  - "MSB3022"
ms.assetid: 74ebcced-8a56-4502-8fef-43d36c79a640
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3022
**在项目文件中，“\<特性\>”和“\<特性\>”同时被指定为输入参数。  请选择其中一个。**  
  
 对于 `Copy` 任务，必须指定 `DestinationFiles` 或 `DestinationDirectory`，而不能同时指定这两个任务特性。  
  
### 更正此错误  
  
-   在项目文件中为 `Copy` 任务指定 `DestinationFiles` 或 `DestinationDirectory`。  
  
## 请参阅  
 [Copy 任务](../msbuild/copy-task.md)   
 [任务](../msbuild/msbuild-tasks.md)