---
title: "FindUnderPath 任务 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "FindUnderPath 任务 [MSBuild]"
  - "MSBuild, FindUnderPath 任务"
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# FindUnderPath 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

确定指定项集合中哪些项的路径位于指定文件夹或指定文件夹的子文件夹中。  
  
## 参数  
 下表描述了 `FindUnderPath` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`Files`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定其路径应当与 `Path` 参数指定的路径进行比较的文件。|  
|`InPath`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 包含在指定路径下找到的项。|  
|`OutOfPath`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 包含未在指定路径下找到的项。|  
|`Path`|必选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指定要用作参考的文件夹路径。|  
|`UpdateToAbsolutePaths`|可选 `Boolean` 参数。<br /><br /> 如果为 true，则将输出项的路径更新为绝对路径。|  
  
## 备注  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 示例  
 下面的示例使用 `FindUnderPath` 任务来确定 `MyFiles` 项中所包含文件的路径是否位于 `SearchPath` 属性指定的路径下。  任务完成后，`FilesNotFoundInPath` 项包含 `File1.txt` 文件，而 `FilesFoundInPath` 项包含 `File2.txt` 文件。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [任务](../msbuild/msbuild-tasks.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)