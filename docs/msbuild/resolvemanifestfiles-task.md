---
title: "ResolveManifestFiles 任务 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f136d6a2ed01e94e2402e0c9b7c381831e99c1e6
ms.lasthandoff: 02/22/2017

---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles 任务
在生成过程中，将以下各项解析为文件以便生成清单：生成项、依赖项、附属项、内容、调试符号和文档。  
  
## <a name="parameters"></a>参数  
 下表描述了 `ResolveManifestFiles` 任务的参数。  
  
|参数|描述|  
|---------------|-----------------|  
|`DeploymentManifestEntryPoint`|可选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指定部署清单的名称。|  
|`EntryPoint`|可选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指定作为清单入口点的托管程序集或 ClickOnce 清单引用。|  
|`ExtraFiles`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定额外文件。|  
|`ManagedAssemblies`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定托管程序集。|  
|`NativeAssemblies`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定本机程序集。|  
|`OutputAssemblies`|可选的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 指定所生成的程序集。|  
|`OutputDeploymentManifestEntryPoint`|可选的 <xref:Microsoft.Build.Framework.ITaskItem> 输出参数。<br /><br /> 指定输出部署清单入口点。|  
|`OutputEntryPoint`|可选的 <xref:Microsoft.Build.Framework.ITaskItem> 输出参数。<br /><br /> 指定输出入口点。|  
|`OutputFiles`|可选的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 指定输出文件。|  
|`PublishFiles`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定发布文件。|  
|`SatelliteAssemblies`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定附属程序集。|  
|`SigningManifests`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则清单已签名。|  
|`TargetCulture`|可选 `String` 参数。<br /><br /> 指定附属程序集的目标区域性。|  
|`TargetFrameworkVersion`|可选 `String` 参数。<br /><br /> 指定目标 .NET Framework 的版本。|  
  
## <a name="remarks"></a>备注  
 除了具有表中列出的参数，此任务还从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身继承自 <xref:Microsoft.Build.Utilities.Task> 类。 有关这些其他参数及其说明的列表，请参阅 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)
