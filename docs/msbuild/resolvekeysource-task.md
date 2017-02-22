---
title: "ResolveKeySource 任务 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ResolveKeySource 任务"
  - "ResolveKeySource 任务 [MSBuild]"
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResolveKeySource 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

确定强名称密钥源。  
  
## 任务参数  
 下表描述了 `ResolveKeySource` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`AutoClosePasswordPromptShow`|可选 `Int32` 参数。<br /><br /> 获取或设置用于显示倒计时消息的时间量（以秒为单位）。|  
|`AutoClosePasswordPromptTimeout`|可选 `Int32` 参数。<br /><br /> 获取或设置在关闭密码提示对话框之前要等待的时间量（以秒为单位）。|  
|`CertificateFile`|可选 `String` 参数。<br /><br /> 获取或设置证书文件的路径。|  
|`CertificateThumbprint`|可选 `String` 参数。<br /><br /> 获取或设置证书指纹。|  
|`KeyFile`|可选 `String` 参数。<br /><br /> 获取或设置密钥文件的路径。|  
|`ResolvedKeyContainer`|可选 `String` 输出参数。<br /><br /> 获取或设置解析的密钥容器。|  
|`ResolvedKeyFile`|可选 `String` 输出参数。<br /><br /> 获取或设置解析的密钥文件。|  
|`ResolvedThumbprint`|可选 `String` 输出参数。<br /><br /> 获取或设置解析的证书指纹。|  
|`ShowImportDialogDespitePreviousFailures`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则无论以前失败与否都应该显示导入对话框。|  
|`SuppressAutoClosePasswordPrompt`|可选 `Boolean` 参数。<br /><br /> 获取或设置一个布尔值，该值指定密码提示对话框是否不应该自动关闭。|  
  
## 备注  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)