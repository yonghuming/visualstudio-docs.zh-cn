---
title: "解决方案概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 06ca562112b8b6feb711219502e3d10b1cb6f462
ms.lasthandoff: 02/22/2017

---
# <a name="solutions-overview"></a>解决方案概述
一种解决方案是协同工作以创建应用程序的一个或多个项目的分组。 与解决方案有关的项目和状态信息存储在两个不同的解决方案文件。 解决方案 (.sln) 文件是基于文本的并可放置在源代码管理下和用户之间共享。 解决方案用户选项 (.suo) 文件是二进制。 结果是，.suo 文件不能将放置在源代码管理下，包含特定于用户的信息。  
  
 任何 VSPackage 可以写入其中任何一种解决方案文件。 由于这些文件的特性，有两个不同的接口实现，以便对其进行写入。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>接口将文本信息写入.sln 文件和<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>接口.suo 文件中写入二进制流。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>  
  
> [!NOTE]
>  不需要显式写入一个条目为自身的解决方案文件; 一个项目环境处理的项目。 因此，除非您想要明确地与解决方案文件添加更多的内容，您不必在这种方式注册你的 VSPackage。  
  
 每个支持解决方案持久性的 VSPackage 使用三个接口<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>接口，它是由的环境实现，并且调用由 VSPackage，和`IVsPersistSolutionProps`和`IVsPersistSolutionOpts`，这些选项均进行同时实现的 VSPackage。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> `IVsPersistSolutionOpts`接口只需将 VSPackage 写入.suo 文件的私人信息是否实现。  
  
 如果打开解决方案时，使用下列过程将会发生。  
  
1.  在环境中读取该解决方案。  
  
2.  如果找到了该环境`CLSID`，它将加载相应的 VSPackage。  
  
3.  加载有 VSPackage 时，环境调用`QueryInterface`为<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>接口，用于 VSPackage 需要的接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>  
  
    1.  当读取.sln 文件，该环境将调用`QueryInterface`为`IVsPersistSolutionProps`。  
  
    2.  当读取.suo 文件，该环境将调用`QueryInterface`为`IVsPersistSolutionOpts`。  
  
 在找不到这些文件的使用相关的特定信息[解决方案 (。Sln) 文件](../../extensibility/internals/solution-dot-sln-file.md)和[解决方案用户选项 (。Suo) 文件](../../extensibility/internals/solution-user-options-dot-suo-file.md)。  
  
> [!NOTE]
>  如果您想要创建新的解决方案配置包含两个项目配置和从生成中排除第三，您需要使用属性页用户界面或自动化。 不能直接更改解决方案生成管理器配置和它们的属性，但您可以处理解决方案生成管理器使用`SolutionBuild`从 DTE 自动化模型中的类。 有关配置解决方案的详细信息，请参阅[解决方案配置](../../extensibility/internals/solution-configuration.md)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
