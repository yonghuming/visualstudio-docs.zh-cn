---
title: "WriteCodeFragment 任务 | Microsoft Docs"
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
  - "MSBuild, WriteCodeFragment 任务"
  - "WriteCodeFragment 任务 [MSBuild]"
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WriteCodeFragment 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

生成从指定的生成代码片段的临时代码文件。  不会删除该文件。  
  
## 参数  
 下表描述 `WriteCodeFragment` 任务的参数。  
  
|参数|说明|  
|--------|--------|  
|`AssemblyAttributes`|选项 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 属性的说明写入的。  项目 `Include` 值是属性的完整类型名称，例如， “System.AssemblyVersionAttribute”。<br /><br /> 每个元数据是该名称\/值对参数，必须为类型 `String`。  某些属性只允许位置的构造函数参数。  但是，在任何属性中使用这些参数。  设置位置的构造函数的属性，请使用类似于 “\_Parameter1”的元数据名称， “\_Parameter2”，依此类推。<br /><br /> 参数索引不能跳过。|  
|`Language`|必需的 `String` 参数。<br /><br /> 指定代码的语言生成。<br /><br /> `Language` 可以是 CodeDom 提供程序可用，例如， “C\#”或 “Visual Basic”的所有语言。  发出的文件将具有该语言的默认文件扩展名。|  
|`OutputDirectory`|选项 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 为生成的代码指定目标文件夹，通常中间文件夹。|  
|`OutputFile`|选项 <xref:Microsoft.Build.Framework.ITaskItem> 输出参数。<br /><br /> 指定生成文件的路径。  通过使用文件名，则此参数设置为，目标文件夹中的前面添加到文件名。  使用根，则设置，目标文件夹被忽略。<br /><br /> 如果此参数未设置，则输出文件名是目标文件夹、一个随机的文件名和默认文件扩展名指定的语言。|  
  
## 备注  
 除了具有外部表中列出的参数，此任务继承 <xref:Microsoft.Build.Tasks.TaskExtension> 类的参数，而从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)