---
title: "任务写入 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 创建任务"
  - "MSBuild, 编写任务"
  - "任务, 为 MSBuild 创建"
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 任务写入
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

这些任务提供在生成过程中运行的代码。  任务包含在目标中。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 附带一个典型任务库，您也可以创建自己的任务。  有关 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 所附带的任务库的更多信息，请参见 [任务参考](../msbuild/msbuild-task-reference.md)。  
  
## 任务  
 任务的示例包括用于复制一个或多个文件的 [Copy](../msbuild/copy-task.md)；用于创建目录的 [MakeDir](../msbuild/makedir-task.md)；以及用于编译 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 源代码文件的 [Csc](../msbuild/csc-task.md)。  每个任务都实现为一个实现 <xref:Microsoft.Build.Framework.ITask> 接口的 .NET 类，该接口在 Microsoft.Build.Framework.dll 程序集中定义。  
  
 实现任务可以采用两种方法：  
  
-   直接实现 <xref:Microsoft.Build.Framework.ITask> 接口。  
  
-   从帮助器类 <xref:Microsoft.Build.Utilities.Task> 派生您的类，该帮助器类在 Microsoft.Build.Utilities.dll 程序集中定义。  任务实现 ITask 并提供某些 ITask 成员的默认实现。  此外，进行日志记录更为简单。  
  
 这两种情况下，都必须向类添加一个名为 `Execute` 的方法，也就是在任务运行时调用的方法。  该方法不带任何参数，返回一个 `Boolean` 值。如果任务成功，则返回 `true`；如果失败，则返回 `false`。  下面的示例显示一个不执行任何操作并返回 `true` 的任务。  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 下面的项目文件运行此任务：  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 如果为任务类创建了 .NET 属性，则在运行任务时，它们也可以从项目文件接收输入。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 设置这些属性，并随后立即调用任务的 `Execute` 方法。  要创建字符串属性，请使用任务代码，例如：  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
         }  
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 下面的项目文件运行此任务并将 `MyProperty` 设置为给定值：  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## 注册任务  
 要使项目能够运行任务，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 必须知道如何找到包含任务类的程序集。  任务是使用 [UsingTask 元素 \(MSBuild\)](../msbuild/usingtask-element-msbuild.md) 注册的。  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 文件 Microsoft.Common.Tasks 是一个包含 `UsingTask` 元素列表的项目文件，这些元素注册随 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 一起提供的所有任务。  在生成每个项目时，会自动包括该文件。  如果在 Microsoft.Common.Tasks 中注册的任务也在当前项目文件中进行了注册，则当前项目文件具有更高的优先级；也就是说，您可以使用自己的同名任务重写默认任务。  
  
> [!TIP]
>  通过查看 Microsoft.Common.Tasks 的内容，可以看到随 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 一起提供的任务的列表。  
  
## 从任务引发事件  
 如果您的任务是从 <xref:Microsoft.Build.Utilities.Task> 帮助器类派生的，可以使用 <xref:Microsoft.Build.Utilities.Task> 类上的下列任一帮助器方法来引发由任何注册的记录器捕获并显示的事件：  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 如果您的任务直接实现 <xref:Microsoft.Build.Framework.ITask>，仍可以引发这样的事件，但是必须使用 IBuildEngine 接口。  下面的示例显示一个实现 ITask 并引发自定义事件的任务：  
  
```  
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## 要求设置任务参数  
 您可以将特定任务的属性标记为“必需”，以便运行该任务的任何项目文件都必须为这些属性设置值，否则生成便会失败。  将 `[Required]` 特性应用到任务的 .NET 属性，如下所示：  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 `[Required]` 特性由 <xref:Microsoft.Build.Framework> 命名空间中的 <xref:Microsoft.Build.Framework.RequiredAttribute> 定义。  
  
## 示例  
  
### 说明  
 下面的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 类演示一个从 <xref:Microsoft.Build.Utilities.Task> 帮助器类派生的任务。  该任务返回 `true`，表示执行成功。  
  
### 代码  
  
```  
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## 示例  
  
### 说明  
 下面的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 类演示一个实现 <xref:Microsoft.Build.Framework.ITask> 接口的任务。  该任务返回 `true`，表示执行成功。  
  
### 代码  
  
```  
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## 示例  
  
### 说明  
 此 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 类演示一个从 <xref:Microsoft.Build.Utilities.Task> 帮助器类派生的任务。  它有一个必需的字符串属性，并引发一个由所有注册的记录器显示的事件。  
  
### 代码  
 [!code-cs[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## 示例  
  
### 说明  
 下面的示例显示一个调用上一个示例任务 SimpleTask3 的项目文件。  
  
### 代码  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)