---
title: "MSBuild 错误 MSB3071 | Microsoft Docs"
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
  - "MSBuild.Exec.AllDriveLettersMappedError"
helpviewer_keywords: 
  - "MSB3071"
ms.assetid: 8afbc6ec-e399-4f06-a30b-f33c87642ef7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3071
**从 A: 到 Z: 的所有驱动器号当前都已被使用。  由于工作目录“\<路径\>”是 UNC 路径，“Exec”任务需要将 UNC 路径映射到一个空闲的驱动器号。  从一个或多个共享资源断开连接以释放驱动器号，或者指定一个本地工作目录，然后再次尝试使用此命令。**  
  
 所有驱动器号（从 A: 到 Z:）都已被使用。  由于指定的工作目录是 UNC 路径，`Exec` 任务需要将 UNC 路径映射到一个空闲的驱动器号。  
  
### 更正此错误  
  
-   从一个或多个共享资源断开连接以释放驱动器号  
  
-   指定一个本地工作目录，然后再次尝试此命令。  
  
## 请参阅  
 [Exec 任务](../msbuild/exec-task.md)