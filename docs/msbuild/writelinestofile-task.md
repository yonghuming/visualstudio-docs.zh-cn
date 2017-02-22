---
title: "WriteLinesToFile 任务 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, WriteLinesToFile 任务"
  - "WriteLinesToFile 任务 [MSBuild]"
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WriteLinesToFile 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

将指定项的路径写入指定的文本文件。  
  
## 任务参数  
 下表描述了 `WriteLinestoFile` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`File`|必选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指定项要写入的文件。|  
|`Lines`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定要写入文件的项。|  
|`Overwrite`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则该任务会覆盖文件中任何现有的内容。|  
|`Encoding`|可选 `String` 参数。<br /><br /> 选择字符编码，例如“unicode”。  另请参见<xref:System.Text.Encoding>。|  
  
## 备注  
 如果 `Overwrite` 为 `true`，则创建一个新文件，向文件中写入内容，然后关闭该文件。  如果目标文件已存在，则覆盖该文件。  如果 `Overwrite` 为 `false`，则将内容追加到文件，如果目标文件还不存在则创建该文件。  
  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 示例  
 下面的示例使用 `WriteLinesToFile` 任务将 `MyItems` 项集合中各项的路径写入 `MyTextFile` 项集合指定的文件。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)