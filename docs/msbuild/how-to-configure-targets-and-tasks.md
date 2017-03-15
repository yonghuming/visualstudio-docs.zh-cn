---
title: "如何：配置目标和任务 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
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
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: ac979e7287046164db37848778f648656f7230a6
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-configure-targets-and-tasks"></a>如何；配置目标和任务
可将所选的 MSBuild 任务设置为在其目标环境中运行，而不考虑开发计算机的环境。 例如，当使用 64 位计算机生成面向 32 位体系结构的应用程序时，将在 32 位进程中运行所选的任务。  
  
> [!NOTE]
>  如果生成任务采用 .NET 语言（例如 Visual C# 或 Visual Basic）编写，并且不使用本机资源或工具，则该任务无需修改便可在任何目标上下文中运行。  
  
## <a name="usingtask-attributes-and-task-parameters"></a>UsingTask 属性和 Task 参数  
 以下 `UsingTask` 属性影响特定生成过程中任务的所有操作：  
  
-   `Runtime` 属性（如果存在）可设置公共语言运行时 (CLR) 版本，并可采用以下值之一：`CLR2`、`CLR4`、`CurrentRuntime` 或 `*`（任何运行时）。  
  
-   `Architecture` 属性（如果存在）可设置平台和位数，并可采用以下值之一：`x86`、`x64`、`CurrentArchitecture` 或 `*`（任何体系结构）。  
  
-   `TaskFactory` 属性（如果存在）可设置创建和运行任务实例的任务工厂，并仅使用值 `TaskHostFactory`。 有关详细信息，请参阅本白皮书后面的“任务工厂”一节。  
  
```xml  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 还可以使用 `MSBuildRuntime` 和 `MSBuildArchitecture` 参数来设置单个任务的目标上下文。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 在 MSBuild 运行任务之前，它将查找具有相同目标上下文的匹配 `UsingTask`。  在 `UsingTask` 中指定的参数（但不在相应的任务中）视为要进行匹配的参数。  在任务中指定的参数（但不在相应的 `UsingTask` 中）也视为要进行匹配的参数。 如果未在 `UsingTask` 或任务中指定参数值，则该值将默认为 `*`（任何参数）。  
  
> [!WARNING]
>  如果存在多个 `UsingTask` 且它们都具有匹配的 `TaskName`、`Runtime` 和 `Architecture` 属性，则要进行评估的最后一个值将替换其他值。  
  
 如果对任务设置参数，则 MSBuild 将尝试查找匹配这些参数或至少不与这些参数冲突的 `UsingTask`。  多个 `UsingTask` 可指定具有相同任务的目标上下文。  例如，针对不同的目标环境具有不同的可执行文件的任务可能类似于：  
  
```xml  
<UsingTask TaskName="MyTool"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />  
  
<UsingTask TaskName="MyTool"   
   Runtime="CLR4"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />  
  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
  
```  
  
## <a name="task-factories"></a>任务工厂  
 在其运行任务之前，MSBuild 将检查该任务是否指定为在当前软件上下文中运行。  如果该任务指定为在当前软件上下文中运行，则 MSBuild 将其传递给 AssemblyTaskFactory（它在当前进程中运行该任务）；否则，MSBuild 将其传递给 TaskHostFactory（它在匹配目标上下文的进程中运行该任务）。 即使当前上下文和目标上下文互相匹配，也可以通过将 `TaskFactory` 设置为 `TaskHostFactory`，强制任务在进程外运行（出于隔离、安全性或其他原因）。  
  
```xml  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## <a name="phantom-task-parameters"></a>虚拟任务参数  
 与任何其他任务参数类似，可以从生成属性设置 `MSBuildRuntime` 和 `MSBuildArchitecture`。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```xml  
  
 Unlike other task parameters, `MSBuildRuntime` and `MSBuildArchitecture` are not apparent to the task itself.  To write a task that is aware of the context in which it runs, you must either test the context by calling the .NET Framework, or use build properties to pass the context information through other task parameters.  
  
> [!NOTE]
>  `UsingTask` attributes can be set from toolset and environment properties.  
  
 The `MSBuildRuntime` and `MSBuildArchitecture` parameters provide the most flexible way to set the target context, but also the most limited in scope.  On the one hand, because they are set on the task instance itself and are not evaluated until the task is about to run, they can derive their value from the full scope of properties available at both evaluation-time and build-time.  On the other hand, these parameters only apply to a particular instance of a task in a particular target.  
  
> [!NOTE]
>  Task parameters are evaluated in the context of the parent node, not in the context of the task host.Environment variables that are runtime- or architecture- dependent (such as the Program files location) will evaluate to the value that matches the parent node.  However, if the same environment variable is read directly by the task, it will correctly be evaluated in the context of the task host.  
  
## See Also  
 [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md)
