---
title: "CPPClean 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.cppclean"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "CPPClean 任务 (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), CPPClean 任务"
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# CPPClean 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

删除在生成 Visual C\+\+ 项目时 MSBuild 创建的临时文件。  删除生成文件的过程称为清洗。  
  
## 参数  
 下表描述了 **CPPClean** 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|**DeletedFiles**|可选 `ITaskItem[]` 输出参数。<br /><br /> 定义可以由任务使用和发出的 MSBuild 输出文件项数组。|  
|**DoDelete**|可选 **Boolean** 参数。<br /><br /> 如果为 `true`，则清理临时生成的文件。|  
|**FilePatternsToDeleteOnClean**|必选 `String` 参数。<br /><br /> 指定要清理的文件的以分号分隔的文件扩展名列表。|  
|**FilesExcludedFromClean**|可选 `String` 参数。<br /><br /> 指定不清理的以分号分隔的文件列表。|  
|**FoldersToClean**|必选 `String` 参数。<br /><br /> 指定要清理的以分号分隔的目录列表。  您可以指定完全或相对的路径，路径可以包含通配符 \(**\***\)。|  
  
## 备注  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)