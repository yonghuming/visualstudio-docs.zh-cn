---
title: "XmlPoke 任务 | Microsoft Docs"
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
helpviewer_keywords: 
  - "MSBuild, XmlPoke 任务"
  - "XmlPoke 任务 [MSBuild]"
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XmlPoke 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

将 XPath 查询指定的值设置为 XML 文件。  
  
## 参数  
 下表描述了 `XmlPoke` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`Namespaces`|可选 `String` 参数。<br /><br /> 指定 XPath 查询的前缀的命名空间。|  
|`Query`|可选 `String` 参数。<br /><br /> 指定 XPath 查询。|  
|`Value`|必选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指定输出文件。|  
|`XmlInputPath`|可选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 以文件路径形式指定 XML 输入。|  
  
## 备注  
 除了有表中列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)