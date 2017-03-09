---
title: "MSBuild 错误 MSB3021 | Microsoft Docs"
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
  - "MSBuild.Copy.Error"
helpviewer_keywords: 
  - "MSB3021"
ms.assetid: 8cb3a860-6916-4406-b5c7-b1106b44b92a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3021
**无法将文件“\<文件\>”复制到文件“\<文件\>”。'  \<错误\>”**  
  
 `Copy` 任务无法复制指定的文件。  
  
### 更正此错误  
  
-   查看目标文件是否被其他应用程序锁定（或使用）。  确保您有权读取源文件，并有权将目标文件写入目标文件夹。  如果目标文件路径非常长，您可能需要复制到其他位置。  
  
## 请参阅  
 [Copy 任务](../msbuild/copy-task.md)   
 [任务](../msbuild/msbuild-tasks.md)