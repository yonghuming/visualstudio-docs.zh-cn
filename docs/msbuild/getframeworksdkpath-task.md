---
title: "GetFrameworkSdkPath 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkSdkPath 任务 [MSBuild]"
  - "MSBuild, GetFrameworkSdkPath 任务"
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# GetFrameworkSdkPath 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

检索 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 的路径。  
  
## 任务参数  
 下表描述了 `GetFrameworkSdkPath` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`FrameworkSdkVersion20Path`|可选 `String` 只读输出参数。<br /><br /> 返回指向 .NET SDK 2.0 版本的路径（如果存在）。  否则，返回 `String.Empty`。|  
|`FrameworkSdkVersion35Path`|可选 `String` 只读输出参数。<br /><br /> 返回指向 .NET SDK 3.5 版本的路径（如果存在）。  否则，返回 `String.Empty`。|  
|`FrameworkSdkVersion40Path`|可选 `String` 只读输出参数。<br /><br /> 返回指向 .NET SDK 4.0 版本的路径（如果存在）。  否则，返回 `String.Empty`。|  
|`Path`|可选 `String` 输出参数。<br /><br /> 包含指向最新 .NET SDK 的路径（如果任何版本存在）。  否则，返回 `String.Empty`。|  
  
## 备注  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 示例  
 下面的示例使用 `GetFrameworkSdkPath` 任务将 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 的路径存储在 `SdkPath` 属性中。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)