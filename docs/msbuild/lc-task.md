---
title: "LC 任务 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 15
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
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 7b4ae3bba069cb1218b4ff1cf0b78877d10dfd34
ms.lasthandoff: 02/22/2017

---
# <a name="lc-task"></a>LC 任务
包装 LC.exe 文件，它可从 .licx 文件生成 .license 文件。 有关 LC.exe 的详细信息，请参阅 [Lc.exe (License Compiler)](http://msdn.microsoft.com/Library/2de803b8-495e-4982-b209-19a72aba0460)（Lc.exe（许可证编译器））。  
  
## <a name="parameters"></a>参数  
 下表描述了 `LC` 任务的参数。  
  
|参数|说明|  
|---------------|-----------------|  
|`LicenseTarget`|必需的 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指定将为其生成 .licenses 文件的可执行文件。|  
|`NoLogo`|可选 `Boolean` 参数。<br /><br /> 取消显示 Microsoft 启动版权标志。|  
|`OutputDirectory`|可选 `String` 参数。<br /><br /> 指定用来放置输出 .licenses 文件的目录。|  
|`OutputLicense`|可选的 <xref:Microsoft.Build.Framework.ITaskItem> 输出参数。<br /><br /> 指定 .licenses 文件的名称。 如果不指定名称，则会使用 .licx 文件的名称，且 .licenses 文件会放在包含此 .licx 文件的目录中。|  
|`ReferencedAssemblies`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定要在生成 .licenses 文件时加载的引用组件。|  
|`SdkToolsPath`|可选 `String` 参数。<br /><br /> 指定 SDK 工具（例如 resgen.exe）的路径。|  
|`Sources`|所需的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定包含许可使用的组件的项，这些组件将要包含在 .licenses 文件中。 有关详细信息，请参阅 [Lc.exe (License Compiler)](http://msdn.microsoft.com/Library/2de803b8-495e-4982-b209-19a72aba0460)（Lc.exe（许可证编译器））中的 `/complist` 开关的文档。|  
  
 除了上面列出的参数，此任务还从 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 类继承参数，此类本身继承自 <xref:Microsoft.Build.Utilities.ToolTask> 类。 有关这些其他参数及其说明的列表，请参阅 [ToolTaskExtension 基类](../msbuild/tooltaskextension-base-class.md)。  
  
## <a name="example"></a>示例  
 下例使用 `LC` 任务来编译许可证。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>另请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)
