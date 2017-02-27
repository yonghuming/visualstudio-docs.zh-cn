---
title: "ResolveComReference 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ResolveCOMReference 任务"
  - "ResolveCOMReference 任务 [MSBuild]"
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# ResolveComReference 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

获取一个或多个类型库名称或 .tlb 文件的列表，将这些类型库解析为磁盘上的位置。  
  
## 参数  
 下表描述了 `ResolveCOMReference` 任务的参数。  
  
|Parameter|描述|  
|---------------|--------|  
|`DelaySign`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则将公钥放入程序集中。  如果为 `false`，则对程序集进行完全签名。|  
|`EnvironmentVariables`|可选 `String[]` 参数。<br /><br /> 等号分隔的环境变量对的数组。  除了将这些变量传递到生成的 tlbimp.exe 和 aximp.exe，还有选择地重写常规环境块。|  
|`ExecuteAsTool`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则将在进程外运行来自相应目标框架的 tlbimp.exe 和 aximp.exe，以生成必要的包装程序集。  此参数可实现多目标功能。|  
|`IncludeVersionInInteropName`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则 typelib 版本将包含在包装名称中。  默认值为 `false`。|  
|`KeyContainer`|可选 `String` 参数。<br /><br /> 指定保存公钥\/私钥的容器<br /><br /> 密钥对。|  
|`KeyFile`|可选 `String` 参数。<br /><br /> 指定包含公钥\/私钥的项<br /><br /> 密钥对。|  
|`NoClassMembers`|可选 `Boolean` 参数。|  
|`ResolvedAssemblyReferences`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 指定已解析的程序集引用。|  
|`ResolvedFiles`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 指定磁盘上与类型库（作为此任务的输入提供）的物理位置对应的完全限定文件。|  
|`ResolvedModules`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。|  
|`SdkToolsPath`|可选 [String](assetId:///String?qualifyHint=False&autoUpgrade=True) 参数。<br /><br /> 如果 `ExecuteAsTool` 为 `true`，则必须将此参数设置为目标框架版本的 SDK 工具路径。|  
|`StateFile`|可选 assetId:///String?qualifyHint=False&autoUpgrade=True 参数。<br /><br /> 指定 COM 组件时间戳的缓存文件。  如果不存在，则每次运行将重新生成所有包装。|  
|`TargetFrameworkVersion`|可选 assetId:///String?qualifyHint=False&autoUpgrade=True 参数。<br /><br /> 指定项目的目标框架版本。<br /><br /> 默认值为 `String.Empty`。  这意味着不存在基于目标框架对引用进行的筛选。|  
|`TargetProcessorArchitecture`|可选 assetId:///String?qualifyHint=False&autoUpgrade=True 参数。<br /><br /> 指定首选的目标处理器结构。  转换后传递到 tlbimp.exe\/计算机标志。<br /><br /> 参数值应为 <xref:Microsoft.Build.Utilities.ProcessorArchitecture> 的成员。|  
|`TypeLibFiles`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定指向 COM 引用的类型库文件路径。  此参数中包括的项可能包含项元数据。  有关更多信息，请参见下面的“TypeLibFiles 项元数据”部分。|  
|`TypeLibNames`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定要解析的类型库名称。  此参数中包括的项必须包含某些项元数据。  有关更多信息，请参见下面的“TypeLibNames 项元数据”部分。|  
|`WrapperOutputDirectory`|可选 `String` 参数。<br /><br /> 生成的互操作程序集放置在磁盘上的位置。  如果未指定此项元数据，任务将使用项目文件所在目录的绝对路径。|  
  
## 备注  
  
## TypeLibNames 项元数据  
 下表描述可供传递给 `TypeLibNames` 参数的项使用的项元数据。  
  
|元数据|描述|  
|---------|--------|  
|`GUID`|必选的项元数据。<br /><br /> 类型库的 GUID。  如果未指定此项元数据，任务将失败。|  
|`VersionMajor`|必选的项元数据。<br /><br /> 类型库的主版本。  如果未指定此项元数据，任务将失败。|  
|`VersionMinor`|必选的项元数据。<br /><br /> 类型库的次版本。  如果未指定此项元数据，任务将失败。|  
|`LocaleIdentifier`|可选的项元数据。<br /><br /> 类型库的区域设置标识符（或 LCID）。  这是作为一个 32 位值指定的，它标识用户、区域或应用程序首选的人类语言。  如果未指定此项元数据，任务将使用默认的区域设置标识符“0”。|  
|`WrapperTool`|可选的项元数据。<br /><br /> 指定用来生成此类型库的程序集包装的包装工具。  如果未指定此项元数据，任务将使用默认的包装工具“tlbimp”。  类型库可用的、不区分大小写的选项为：<br /><br /> -   `Primary`：当您想要为 COM 组件使用已生成的主互操作程序集时，请使用此包装工具。  使用此包装工具时，请不要指定包装输出目录，因为这将导致任务失败。<br />-   `TLBImp`：当您想要为 COM 组件生成一个互操作程序集时，请使用此包装工具。<br />-   `AXImp`:，在希望生成 ActiveX 控件时，一个互操作程序集使用此包装工具。|  
  
## TypeLibFiles 项元数据  
 下表描述可供传递给 `TypeLibFiles` 参数的项使用的项元数据。  
  
|元数据|描述|  
|---------|--------|  
|`WrapperTool`|可选的项元数据。<br /><br /> 指定用来生成此类型库的程序集包装的包装工具。  如果未指定此项元数据，任务将使用默认的包装工具“tlbimp”。  类型库可用的、不区分大小写的选项为：<br /><br /> -   `Primary`：当您想要为 COM 组件使用已生成的主互操作程序集时，请使用此包装工具。  使用此包装工具时，请不要指定包装输出目录，因为这将导致任务失败。<br />-   `TLBImp`：当您想要为 COM 组件生成一个互操作程序集时，请使用此包装工具。<br />-   `AXImp`:，在希望生成 ActiveX 控件时，一个互操作程序集使用此包装工具。|  
  
> [!NOTE]
>  提供的可唯一地标识类型库的信息越多，任务解析出磁盘上的正确文件的可能性就越大。  
  
## 备注  
 除了以上列出的参数外，此任务还从 <xref:Microsoft.Build.Utilities.Task> 类继承参数。  有关这些附加参数及其说明的列表，请参见 [任务基类](../msbuild/task-base-class.md)。  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)