---
title: "公开到可视化设计器的类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "可视化设计器向公开的类型 [Visual Studio SDK]"
  - "设计器 [Visual Studio SDK]，公开的类型"
  - "公开到可视化设计器的类型的自定义工具"
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 公开到可视化设计器的类型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必须具有访问权限的类，并在设计的类型定义超时以便显示可视化设计器。  从加载预定义的类包括完整的依赖项设置当前项目的程序集 \(引用以及它们的依赖项\)。  可能还需要为可视化设计器到自定义工具生成的文件中定义的访问类和类型。  
  
 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 和 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 项目系统提供访问生成的类和类型支持通过临时可移植可执行文件 \(临时 PE\)。  自定义工具生成的所有文件都编译到一个临时程序集，以使类型可以从这些程序集加载并显示在设计器。  每个自定义工具输出编译到单独的临时 PE，因此，该临时生成的成功或失败取决于只生成的文件是否可生成。  整体即使项目就无法生成，单个临时 PE 仍可供设计器。  
  
 ，这些更改是运行自定义工具条件下的结果，项目系统提供用于跟踪对自定义工具的输出文件的更改的完全支持。  每次自定义工具运行，新的临时 PE 生成，因此，相应的通知发送到设计器。  
  
> [!NOTE]
>  由于临时程序可执行文件生成文件在后台执行，错误不向用户报告，如果生成失败。  
  
 利用临时 PE 的自定义工具支持必须遵循下列规则:  
  
-   必须设置`GeneratesDesignTimeSource` 到 1 在注册表中。  
  
     程序可执行文件生成不会发生无需此设置。  
  
-   生成的代码必须在语言和全局项目设置相同。  
  
     临时 PE 编译无论自定义工具报告为 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> 的请求的扩展，在 `GeneratesDesignTimeSource` 设置为 1 在注册表条件下。  该扩展不必是 .vb、 .cs 或 .jsl;它可以是任何扩展。  
  
-   自定义工具生成的代码必须是有效的，因此，它必须生成只用于设置独立项目中引用的存在，在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 完成执行时间。  
  
     当临时 PE 编译时，唯一的源文件提供给编译器是自定义工具输出。  因此，使用一个临时 PE 的自定义工具必须生成可以依赖于该项目的其他文件生成的输出文件。  
  
## 请参阅  
 [Introduction to the BuildManager Object](http://msdn.microsoft.com/zh-cn/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [实现单文件生成器](../../extensibility/internals/implementing-single-file-generators.md)   
 [确定项目的默认命名空间](../../misc/determining-the-default-namespace-of-a-project.md)   
 [注册的单文件生成器](../../extensibility/internals/registering-single-file-generators.md)