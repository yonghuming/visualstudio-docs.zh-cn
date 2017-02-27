---
title: "AssignProjectConfiguration 任务 | Microsoft Docs"
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
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
caps.latest.revision: 7
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
ms.openlocfilehash: 80fe9e734dd8af527fad318df17f9c456129d660

---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration 任务
此任务接受列表配置字符串，并将其分配给指定的项目。  
  
## <a name="task-parameters"></a>任务参数  
 下表描述了 `AssignProjectConfiguration` 任务的参数。  
  
|参数|描述|  
|---------------|-----------------|  
|`SolutionConfigurationContents`|可选 `string` 输出参数。<br /><br /> 包含 XML 字符串，该字符串包含每个项目的项目配置。 这些配置分配给已命名的项目。|  
|`DefaultToVcxPlatformMapping`|可选 `string` 输出参数。<br /><br /> 包含以分号分隔的映射列表，这些映射是从由大多数类型所使用的平台名称<br /><br /> 到由 .vcxproj 文件所使用的平台名称的映射。<br /><br /> 例如: <br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|  
|`VcxToDefaultPlatformMapping`|Optional<br /><br /> `string` 输出参数。<br /><br /> 包含以分号分隔的映射列表，这些映射是从 .vcxproj 平台名称到由大多数类型所使用的平台名称的映射。<br /><br /> 例如: <br /><br /> `"Win32=AnyCPU;X64=X64"`|  
|`CurrentProjectConfiguration`|可选 `string` 输出参数。<br /><br /> 包含当前项目的配置。|  
|`CurrentProjectPlatform`|可选 `string` 输出参数。<br /><br /> 包含当前项目的平台。|  
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|可选 `bool` 输出参数。<br /><br /> 包含指示应生成引用（即使在项目配置中禁用引用）的标志。|  
|`ShouldUnsetParentConfigurationAndPlatform`|可选 `bool` 输出参数。<br /><br /> 包含指示是否应取消设置父级配置和平台的标志。|  
|`OutputType`|可选 `string` 输出参数。<br /><br /> 包含项目的输出类型。|  
|`ResolveConfigurationPlatformUsingMappings`|可选 `bool` 输出参数。<br /><br /> 包含指示生成是否应使用默认映射来解析项目引用中传递的配置和平台的标志。|  
|`AssignedProjects`|可选的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 包含解析引用路径的列表。|  
|`UnassignedProjects`|可选的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 包含项目引用项的列表，其中这些项无法使用输出的预解析列表进行解析。|  
  
## <a name="remarks"></a>备注  
 除了上面列出的参数，此任务还从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身继承自 <xref:Microsoft.Build.Utilities.Task> 类。 有关这些其他参数及其说明的列表，请参阅 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)


<!--HONumber=Feb17_HO4-->


