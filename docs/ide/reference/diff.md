---
title: "/Diff | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Diff
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

比较两个文件。  差异在特定 Visual Studio 窗口中显示。  
  
## 语法  
  
```  
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],  
[TargetDisplayName]  
```  
  
## 实参  
 `SourceFile`  
 必需。  要比较的第一个文件的完整路径和名称。  
  
 `TargetFile`  
 必需。  要比较的第二个文件的完整路径和名称  
  
 `SourceDisplayName`  
 可选。  第一个文件的显示名称。  
  
 `TargetDisplayName`  
 可选。  第二个文件的显示名称。