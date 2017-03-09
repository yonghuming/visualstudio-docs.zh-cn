---
title: "MSBuild 错误 MSB3072 | Microsoft Docs"
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
  - "MSBuild.Exec.MissingCommandError"
helpviewer_keywords: 
  - "MSB3072"
ms.assetid: c8468e1c-d8c7-441c-b274-123ac856f147
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3072
**“Exec”任务需要使用命令来执行。**  
  
 特性 `Command` 是 `Exec` 任务的一个必需特性。  
  
### 更正此错误  
  
1.  在项目文件中，为 `Exec` 任务指定特性 `Command`。  
  
## 请参阅  
 [Exec 任务](../msbuild/exec-task.md)   
 [任务](../msbuild/msbuild-tasks.md)