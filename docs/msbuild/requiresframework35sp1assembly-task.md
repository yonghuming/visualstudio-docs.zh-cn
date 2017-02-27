---
title: "RequiresFramework35SP1Assembly 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "MSBuild, RequiresFramework35SP1Assembly 任务"
  - "RequiresFramework35SP1Assembly 任务 [MSBuild]"
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# RequiresFramework35SP1Assembly 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

确定应用程序是否需要 .NET framework 3.5 SP1。  
  
## 参数  
 下表描述 `RequiresFramework35SP1Assembly` 任务的参数。  
  
|参数|说明|  
|--------|--------|  
|`Assemblies`|选项 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定在应用程序引用的程序集。|  
|`CreateDesktopShortcut`|选项 `Boolean` 参数。<br /><br /> 如果 `true`，在安装时创建桌面上的快捷方式图标。|  
|`DeploymentManifestEntryPoint`|选项 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 为应用程序指定该清单文件名。|  
|`EntryPoint`|选项 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指定应执行的程序集，当应用程序运行时。|  
|`ErrorReportUrl`|选项 `String` 参数。<br /><br /> 指定在 ClickOnce 安装过程中，显示在对话框中遇到的网站。|  
|`Files`|选项 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定要部署的文件列表，当应用程序发布时。|  
|`ReferencedAssemblies`|选项 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定在项目引用的程序集。|  
|`RequiresMinimumFramework35SP1`|选项 `Boolean` 输出参数。<br /><br /> 如果 `true`，应用程序需要 .NET framework 3.5 SP1。|  
|`SigningManifests`|选项 `Boolean` 输出参数。<br /><br /> 如果 `true`， ClickOnce 清单进行签名。|  
|`SuiteName`|选项 `String` 参数。<br /><br /> 在应用程序安装的 **启动** 菜单指定文件夹的名称。|  
|`TargetFrameworkVersion`|选项 `String` 参数。<br /><br /> 指定 .NET framework 的版本此应用程序目标。|  
  
## 备注  
 除了具有外部表中列出的参数，此任务继承 <xref:Microsoft.Build.Tasks.TaskExtension> 类的参数，而从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)