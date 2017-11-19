---
title: "项目输出的配置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b19b3956e03c23d70852d8a2297544a72d91b840
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-configuration-for-output"></a>输出的项目配置
每个配置可支持一组生成输出项，如可执行文件或资源文件的生成进程。 这些输出项专用于用户，并可以放在链接的输出，如可执行文件 （.exe、.dll 或.lib） 和源文件 （.idl，.h 文件） 的相关的类型的组中。  
  
 输出项可提供通过<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2>方法和使用枚举<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>方法。 如果你想对输出项进行分组，你的项目还应实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>接口。  
  
 通过实现构造开发`IVsOutputGroup`允许根据使用情况的组输出到的项目。 例如，一个 DLL 可能与其程序数据库 (PDB) 分组。  
  
> [!NOTE]
>  PDB 文件包含调试信息并生成.dll 或.exe 时指定生成调试信息选项时创建它。 .Pdb 文件通常生成调试项目配置。  
  
 项目必须返回相同数量的支持，每个配置的组，即使的组中包含的输出数可能不同 configuration 配置也是如此。 例如，项目 Matt 的 DLL 可能在调试配置中，包括 mattd.dll 和 mattd.pdb，但仅将 matt.dll 包含零售配置中。  
  
 组还具有相同的标识符信息，如规范名称、 显示名称和组信息配置配置项目中。 这种一致性允许部署和打包以继续运行，即使配置更改。  
  
 组还可以具有允许打包快捷方式以指向有意义的内容密钥输出。 因此应有关组的大小不进行任何假设，任何组可能在给定的配置中，为空。 在任何配置中的每个组的大小 （的输出数） 可以在同一配置的另一个组的大小不同。 它还可在另一个配置相同的组的大小不同。  
  
 ![输出组图形](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
输出组  
  
 主要用途<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg>接口是来提供访问生成、 部署和调试管理对象和允许到组输出自由的项目。 使用此接口的详细信息，请参阅[项目配置对象](../../extensibility/internals/project-configuration-object.md)。  
  
 在上图中，组生成都有一个键，因此输出配置 （bD.exe 或 b.exe） 跨用户能够创建内置的快捷方式，了解快捷方式将工作而不考虑部署配置。 组源没有输出，一个密钥，因此用户将无法创建它的快捷方式。 如果调试组生成有主要输出，但零售组生成没有，为不正确的实现。 下述，然后，如果任何配置有包含不到输出，一个组，并因此，没有密钥的文件，然后其他配置与该组包含输出不能具有密钥文件。 安装程序编辑器假定规范名称和显示名称的组，以及存在的密钥文件，不要更改基于配置中。  
  
 请注意，如果一个项目具有`IVsOutputGroup`，它不希望打包或部署，只需将该输出放在一个组。 输出可以仍枚举通常通过实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A>返回所有配置的输出，而不考虑分组的方法。  
  
 有关详细信息，请参阅的实现`IVsOutputGroup`中的自定义项目示例[项目的 MPF](http://mpfproj12.codeplex.com)。  
  
## <a name="see-also"></a>另请参阅  
 [管理配置选项](../../extensibility/internals/managing-configuration-options.md)   
 [生成的项目配置](../../extensibility/internals/project-configuration-for-building.md)   
 [项目配置对象](../../extensibility/internals/project-configuration-object.md)   
 [解决方案配置](../../extensibility/internals/solution-configuration.md)