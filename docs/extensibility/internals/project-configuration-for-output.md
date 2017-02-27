---
title: "输出的项目配置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目配置、 输出"
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 输出的项目配置
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

每个配置可以支持一套生成输出项，如可执行文件或资源文件的生成过程。 这些输出项是私有的用户，可以放在链接相关的类型的输出，如可执行文件 \(.exe、.dll、.lib\) 和源文件 \(.idl、.h 文件\) 的组中。  
  
 输出项便可通过提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> 方法和使用枚举 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> 方法。 如果希望输出项进行分组，您的项目还应实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> 接口。  
  
 实现由该构造 `IVsOutputGroup` 允许到组输出根据使用情况的项目。 例如，一个 DLL 可能与其程序数据库 \(PDB\) 分组。  
  
> [!NOTE]
>  PDB 文件包含调试信息并生成.dll 或.exe 时指定生成调试信息选项时创建它。 .Pdb 文件通常是调试项目配置为生成的。  
  
 项目必须返回相同数量的支持，每个配置的组，即使包含在组中的输出数可能不同配置配置也是如此。 例如，项目 Matt 的 DLL 可能会在调试配置中，包括 mattd.dll 和 mattd.pdb，但只在零售配置中包括 matt.dll。  
  
 组还具有相同标识符的信息，如规范名称、 显示名称和组信息，配置配置项目中。 这种一致性允许部署和打包以继续运行，即使更改了配置。  
  
 组还可以具有允许打包快捷方式，以指向有意义的内容密钥输出。 任何组可能在给定配置中，为空，因此任何假设应不成为有关的一组大小。 任何配置中每个组的大小 \(多个输出\) 可以是相同的配置中的其他组的大小不同。 这也可以是另一种配置中的相同组的大小不同。  
  
 ![图：输出组](../../extensibility/internals/media/vsoutputgroups.png "vsOutputGroups")  
输出组  
  
 主要用途 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> 接口是提供访问以生成、 部署和调试管理对象和允许到组输出自由的项目。 使用此接口的详细信息，请参阅 [项目配置对象](../../extensibility/internals/project-configuration-object.md)。  
  
 在上图中，组生成都有一个密钥，因此输出配置 \(bD.exe 或 b.exe\) 在用户可以创建的快捷方式进行构建，并知道快捷方式将工作而不考虑部署的配置。 组源没有输出，一个密钥，因此用户不能创建它的快捷方式。 如果调试组生成有主要输出，但零售组生成没有，这将是不正确的实现。 规则是，然后，如果任何配置都有一组包含没有输出和结果是，没有密钥的文件，则其他与该组的配置包含输出不能具有密钥文件。 安装程序编辑器假定，规范名称和显示名称的组，以及存在一个密钥文件，不会更改基于在配置中。  
  
 请注意，如果一个项目具有 `IVsOutputGroup` ，它不想打包或部署，只需将该输出放在一个组。 输出仍可枚举通常通过实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> 返回所有配置的输出，而不考虑分组的方法。  
  
 有关详细信息，请参阅的实现 `IVsOutputGroup` 在自定义项目示例中 [项目的 MPF](http://mpfproj12.codeplex.com)。  
  
## 请参阅  
 [管理配置选项](../../extensibility/internals/managing-configuration-options.md)   
 [生成的项目配置](../../extensibility/internals/project-configuration-for-building.md)   
 [项目配置对象](../../extensibility/internals/project-configuration-object.md)   
 [解决方案配置](../../extensibility/internals/solution-configuration.md)