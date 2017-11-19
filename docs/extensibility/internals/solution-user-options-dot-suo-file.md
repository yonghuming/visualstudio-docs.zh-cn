---
title: "解决方案用户选项 (。Suo) 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a71f3e14c6a8c87290de2a6204fa28f99a8cabe8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="solution-user-options-suo-file"></a>解决方案用户选项 (。Suo) 文件
解决方案用户选项 (.suo) 文件包含每个用户解决方案选项。 此文件应不会签入到源代码管理。  
  
 解决方案用户选项 (.suo) 文件是一个结构化的存储或复合，以二进制格式存储的文件。 你正在将用于标识.suo 文件中的信息的密钥的流的名称保存到流的用户信息。 解决方案用户选项文件可用于存储用户首选项设置，并在 Visual Studio 将保存解决方案时自动创建。  
  
 当环境将打开.suo 文件时，它枚举所有当前加载的 Vspackage。 如果 VSPackage 实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>接口，然后，该环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A>VSPackage 要求它从.suo 文件加载其所有数据上的方法。  
  
 很可能具有 VSPackage 的责任知道什么流写入到.suo 文件。 对于每个流，它已写入，VSPackage 调用返回到环境中，通过<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>加载键，即流的名称标识的特定流。 环境然后回拨到 VSPackage 可以读取将流的名称传递该特定流和`IStream`指向<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>方法。  
  
 此时，另一个调用`LoadUserOptions`以查看是否具有要读取的.suo 文件的另一部分。 此过程将继续，直到所有.suo 文件中的数据流已读取和处理环境。  
  
 当解决方案不保存或关闭，环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A>用一个指针指向方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>方法。 `IStream`包含要保存二进制信息传递给<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>方法，然后将信息写入的.suo 文件和调用`SaveUserOptions`方法以查看是否有另一个流的信息写入到.suo文件。  
  
 这两种方法，`SaveUserOptions`和`WriteUserOptions`，以递归方式调用的信息保存到.suo 文件，传递到指针中的每个流`IVsSolutionPersistence`。 它们分别名以递归方式以允许写入的.suo 文件的多个流。 以这种方式，用户信息将保留与解决方案，并保证在那里在下次打开该解决方案。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [解决方案](../../extensibility/internals/solutions.md)