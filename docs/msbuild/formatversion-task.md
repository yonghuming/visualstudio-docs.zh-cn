---
title: "FormatVersion 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# FormatVersion 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

将修订版本号附加到版本号上。  
  
-   案例 1：输入：版本 \= \<未定义\>；修订 \= \<无关紧要\>；输出：OutputVersion \=“1.0.0.0”  
  
-   案例 2：输入：版本 \=“1.0.0.\*”修订 \=“5”输出：OutputVersion \=“1.0.0.5”  
  
-   案例 3：输入：版本 \=“1.0.0.0”；修订 \= \<无关紧要\>；输出：OutputVersion \=“1.0.0.0”  
  
## 参数  
 下表描述了 `FormatVersion` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`FormatType`|可选 `String` 参数。<br /><br /> 指定格式类型。<br /><br /> -   “版本”\= version。<br />-   “路径”\= 将“.”替换为“\_”；|  
|`OutputVersion`|可选 `String` 输出参数。<br /><br /> 指定包含修订版本号的输出版本。|  
|`Revision`|可选 `Int32` 参数。<br /><br /> 指定要追加到版本中的修订。|  
|`Version`|可选 `String` 参数。<br /><br /> 指定要格式化的版本号字符串。|  
  
## 备注  
 除了有表中列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)