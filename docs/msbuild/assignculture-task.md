---
title: "AssignCulture 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "AssignCulture 任务 [MSBuild]"
  - "MSBuild, AssignCulture 任务"
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# AssignCulture 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此任务接受一组可能在文件名中包含有效的 .NET 区域性标识符字符串的项，并生成具有名为 `Culture` 的元数据（包含相应的区域性标识符）的项。  例如，文件名 Form1.fr\-fr.resx 嵌入了区域性标识符“fr\-fr”，因此，此任务将产生一个具有相同文件名、并且元数据 `Culture` 等于 `fr-fr` 的项。  该任务还产生一组文件名，这些文件名中的区域性已被移除。  
  
## 任务参数  
 下表描述了 `AssignCulture` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`AssignedFiles`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 包含通过 `Files` 参数接收到的项列表，其中的每一项都添加了 `Culture` 元数据项。<br /><br /> 如果从 `Files` 参数传入的项已经包含 `Culture` 元数据项，将使用最初的元数据项。<br /><br /> 该任务将只有在文件名包含有效的区域性标识符时才分配 `Culture` 元数据项。  区域性标识符必须位于文件名中最后两个点之间。|  
|`AssignedFilesWithCulture`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 包含 `AssignedFiles` 参数中各项的子集，这些项具有 `Culture` 元数据项。|  
|`AssignedFilesWithNoCulture`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 包含 `AssignedFiles` 参数中各项的子集，这些项没有 `Culture` 元数据项。|  
|`CultureNeutralAssignedFiles`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 包含同一个在 `AssignedFiles` 参数中产生的项列表，只是区域性已从文件名中移除。<br /><br /> 只有当区域性是有效的区域性标识符时，此任务才将它从文件名中移除。|  
|`Files`|必选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定要为其分配区域性并且嵌入了区域性名称的文件的列表。|  
  
## 备注  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 示例  
 下面的示例使用 `ResourceFiles` 项集合执行 `AssignCulture` 任务。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 下表描述了任务执行后各输出项的值。  项的元数据显示在该项后面的括号中。  
  
|项集合|内容|  
|---------|--------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx`（无附加元数据）|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx`（无附加元数据）|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`（无附加元数据）|  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)