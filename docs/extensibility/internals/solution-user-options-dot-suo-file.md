---
title: "解决方案用户选项 (。Suo) 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".suo 文件 Vspackage"
  - "suo 文件 Vspackage"
  - ".suo 文件的解决方案"
  - "解决方案用户选项"
  - "解决方案用户选项 (.suo) 文件"
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 解决方案用户选项 (。Suo) 文件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

解决方案用户选项 \(.suo\) 文件包含每个用户的解决方案的选项。 此文件应不会签入到源代码管理。  
  
 解决方案用户选项 \(.suo\) 文件是结构化的存储或复合，二进制格式存储文件中。 正在将用于标识.suo 文件中的信息的键的流的名称与保存到流的用户信息。 解决方案用户选项文件用于存储用户首选项设置，并在 Visual Studio 将保存在一个解决方案时自动创建。  
  
 当环境打开.suo 文件时，它将枚举所有当前加载的 Vspackage。 如果实现了 VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> 接口，然后环境调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> VSPackage 要求它.suo 文件中加载其数据的所有方法。  
  
 很可能已知道什么流的 VSPackage 的责任写入到.suo 文件。 对于每个流，它编写，VSPackage 调用返回到环境中，通过 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 加载由键，这是流的名称标识的特定流。 环境然后回拨到 VSPackage 来读取该特定流传递的流的名称和一个 `IStream` 指针，指向 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 方法。  
  
 到那时，供另一次调用 `LoadUserOptions` 以查看是否具有要读取的.suo 文件的另一部分。 .Suo 文件中的数据流的所有已读取并处理由环境之前，此过程将继续。  
  
 在保存或关闭环境调用解决方案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> 用一个指针指向方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> 方法。`IStream` 包含要保存的二进制信息传递给 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> 方法，然后将信息写入.suo 文件并调用 `SaveUserOptions` 方法再次以查看是否有要写入到.suo 文件的信息的另一个流。  
  
 这两种方法， `SaveUserOptions` 和 `WriteUserOptions`, ，为每个流保存到.suo 文件中，在将指针与中传递信息以递归方式调用 `IVsSolutionPersistence`。 调用以递归方式写入的.suo 文件的多个流允许它们。 这样一来，用户信息与解决方案一起持久保留，并保证会在下次打开该解决方案。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [解决方案](../../extensibility/internals/solutions.md)