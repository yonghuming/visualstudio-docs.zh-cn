---
title: "解决方案概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6a1afea2357fb0c0ef1bcf8152f8a3785a55786
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="solutions-overview"></a>解决方案概述
解决方案是协同工作以创建应用程序的一个或多个项目中的分组。 与解决方案相关的项目和状态信息存储在两个不同的解决方案文件。 解决方案 (.sln) 文件是基于文本的和可以放置在源代码管理下和用户之间共享。 解决方案用户选项 (.suo) 文件是二进制。 因此，.suo 文件不能将放置在源代码管理下，并包含特定于用户的信息。  
  
 任何 VSPackage 可以写入其中任何一种解决方案文件。 由于这些文件的性质，有两个不同的接口实现以对其进行写入。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>接口将文本信息写入.sln 文件和<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>接口.suo 文件中写入二进制流。  
  
> [!NOTE]
>  不需要显式写入一个条目为其自身的解决方案文件; 一个项目环境处理的项目。 因此，除非你想要将更多的内容添加到解决方案文件的具体而言，你不必在这种方式中注册你的 VSPackage。  
  
 每个 VSPackage 支持解决方案持久性使用三个接口，<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>接口，此操作是由的环境实现，并且调用由 VSPackage，和`IVsPersistSolutionProps`和`IVsPersistSolutionOpts`，这些选项均进行同时实现由 VSPackage。 `IVsPersistSolutionOpts`接口只需如果私有信息是由 VSPackage 写入.suo 文件要实现。  
  
 当打开解决方案时，使用下列过程将发生。  
  
1.  环境读取解决方案。  
  
2.  如果环境找到`CLSID`，它将加载相应的 VSPackage。  
  
3.  如果 VSPackage 加载时，环境调用`QueryInterface`为<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>接口的接口，VSPackage 要求。  
  
    1.  在读取从.sln 文件时，则环境将调用`QueryInterface`为`IVsPersistSolutionProps`。  
  
    2.  在读取从.suo 文件，则环境将调用`QueryInterface`为`IVsPersistSolutionOpts`。  
  
 与这些文件的使用相关的特定信息，请查看[解决方案 (。Sln) 文件](../../extensibility/internals/solution-dot-sln-file.md)和[解决方案用户选项 (。Suo) 文件](../../extensibility/internals/solution-user-options-dot-suo-file.md)。  
  
> [!NOTE]
>  如果你想要创建新的解决方案配置包含两个项目的配置和生成中排除第三个，你需要使用的属性页 UI 或自动化。 你无法直接更改解决方案生成管理器配置和及其属性，但你可以操作使用的解决方案生成管理器`SolutionBuild`从 DTE 自动化模型中的类。 有关配置解决方案的详细信息，请参阅[解决方案配置](../../extensibility/internals/solution-configuration.md)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>