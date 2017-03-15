---
title: "VCMessage 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.vcmessage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), VCMessage 任务"
  - "VCMessage 任务 (MSBuild (Visual C++))"
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# VCMessage 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

生成期间产生的警告和错误消息日志。  
  
## 备注  
 此任务可以帮助实现 Visual C\+\+ 的 MSBuild 并不应由用户调用。  有关更多信息，请参见 <xref:Microsoft.Build.Utilities.TaskLoggingHelper>。  
  
## 参数  
 下表描述了 **VCMessage** 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|**Arguments**|可选 **String** 参数。<br /><br /> 要显示的以分号分隔信息的列表。|  
|**Code**|必选 **String** 参数。<br /><br /> 限定消息的错误号码。|  
|**Type**|可选 **String** 参数。<br /><br /> 指定要发出的消息的种类。  指定`“警告”`以发出警告信息，或指定`“错误”`发出错误信息。|  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)