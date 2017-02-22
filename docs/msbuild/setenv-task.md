---
title: "SetEnv 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.setenv"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), 任务"
  - "SetEnv 任务 (MSBuild (Visual C++))"
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# SetEnv 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

设置或删除指定环境变量的值。  
  
## 参数  
 下表描述了 **SetEnv** 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|**Name**|必选 **String** 参数。<br /><br /> 环境变量名。|  
|**OutputEnvironmentVariable**|可选 **String** 输出参数。<br /><br /> 包含分配给 **Name** 参数指定的环境变量的值。|  
|**Prefix**|强制 `Boolean` 参数。<br /><br /> `true` 和 **Value** 参数指定的环境变量的值；或者如果找不到环境变量，则返回 **Name**。  如果为 `false`，则只会将 **Value** 参数的值分配给环境变量。|  
|**Target**|可选 **String** 参数。<br /><br /> 指定存储环境变量的位置。  指定“`用户`”或“`计算机`”。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上的“EnvironmentVariableTarget Enumeration”（EnvironmentVariableTarget 枚举）。|  
|**Value**|可选 **String** 参数。<br /><br /> 分配给 **Name** 参数指定的环境变量的值。  如果 **Value** 为空且变量存在，则删除该变量。  如果变量不存在，则即使无法执行该操作也不会发生错误。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上的“Environment::SetEnvironmentVariable Method”（Environment::SetEnvironmentVariable 方法）。|  
  
## 备注  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)