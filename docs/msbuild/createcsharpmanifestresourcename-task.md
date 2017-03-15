---
title: "CreateCSharpManifestResourceName 任务 | Microsoft Docs"
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
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
caps.latest.revision: 8
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
ms.openlocfilehash: 574e04aa1c741c0a1720adf3fc77c2765f9dc1d3
ms.lasthandoff: 02/22/2017

---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName 任务
从给定的 .resx 文件名或其他资源创建 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 样式的清单名称。  
  
## <a name="parameters"></a>参数  
 下表描述 [CreateCSharpManifestResourceName 任务](../msbuild/createcsharpmanifestresourcename-task.md)的参数。  
  
|参数|说明|  
|---------------|-----------------|  
|`ManifestResourceNames`|<xref:Microsoft.Build.Framework.ITaskItem> `[]` 输出只读参数。<br /><br /> 生成的清单名称。|  
|`ResourceFiles`|必选 `String` 参数。<br /><br /> 从中创建 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 清单名称的资源文件名称。|  
|`RootNamespace`|可选 `String` 参数。<br /><br /> 资源文件的根命名空间，通常取自于项目文件。 可为 `null`。|  
|`PrependCultureAsDirectory`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则将区域性名称作为目录名称添加到清单资源名称前。 默认值为 `true`。|  
|`ResourceFilesWithManifestResourceNames`|可选的 `String` 只读输出参数。<br /><br /> 返回现在包括清单资源名称的资源文件的名称。|  
  
## <a name="remarks"></a>备注  
 [CreateVisualBasicManifestResourceName 任务](../msbuild/createvisualbasicmanifestresourcename-task.md)决定了要分配到给定 .resx 或其他资源文件的相应清单资源名称。 该任务向资源文件提供一个逻辑名称，然后将其作为元数据附加到输出参数。  
  
 除了上面列出的参数，此任务还从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身继承自 <xref:Microsoft.Build.Utilities.Task> 类。 有关这些其他参数及其说明的列表，请参阅 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)
