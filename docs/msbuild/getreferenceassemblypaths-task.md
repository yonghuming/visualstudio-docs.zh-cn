---
title: "GetReferenceAssemblyPaths 任务 | Microsoft Docs"
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
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 4
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 11a9cee75f912c5fb31cf4a031644abe9c63d744
ms.openlocfilehash: 6009ccb21696e207facfe6c172d4c131f13f8bc0
ms.contentlocale: zh-cn
ms.lasthandoff: 06/03/2017

---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths 任务
返回各种框架的引用程序集路径。  
  
## <a name="parameters"></a>参数  
 下表描述了 `GetReferenceAssemblyPaths` 任务的参数。  
  
|参数|描述|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|可选 `String[]` 输出参数。<br /><br /> 基于 `TargetFrameworkMoniker` 参数返回路径。 如果 `TargetFrameworkMoniker` 为 null 或为空，则此路径将为 `String.Empty`。|  
|`FullFrameworkReferenceAssemblyPaths`|可选 `String[]` 输出参数。<br /><br /> 基于 `TargetFrameworkMoniker` 参数返回路径，无需考虑名字对象的配置文件部分。 如果 `TargetFrameworkMoniker` 为 null 或为空，则此路径将为 `String.Empty`。|  
|`TargetFrameworkMoniker`|可选 `String` 参数。<br /><br /> 指定与引用程序集路径关联的目标框架名字对象。|  
|`RootPath`|可选 `String` 参数。<br /><br /> 指定用于生成引用程序集路径的根路径。|  
|`BypassFrameworkInstallChecks`|可选 <xref:System.Boolean> 参数。<br /><br /> 如果为 `true`，则绕过基本检查。默认情况下，`GetReferenceAssemblyPaths` 执行这些基本检查是为了确保已根据目标框架安装了某些运行时框架。|  
|`TargetFrameworkMonikerDisplayName`|可选 `String` 输出参数。<br /><br /> 指定目标框架名字对象的显示名称。|  
  
## <a name="remarks"></a>备注  
 除了具有表中列出的参数外，此任务还将从本身继承自 <xref:Microsoft.Build.Utilities.Task> 类的 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数。 有关这些其他参数的列表及其说明的信息，请参阅 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)
