---
title: "公开到可视化设计器的类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e79ec644426ed5068f79bb914b1202a800982cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="exposing-types-to-visual-designers"></a>公开到可视化设计器的类型
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必须有权类和类型定义在设计时为了显示可视化设计器中。 类将从一组预定义的包含完整的依赖项集的当前项目 （引用加上其依赖项） 的程序集加载。 此外可能有必要对可视化设计器的访问权限类和在自定义工具生成的文件中定义的类型。  
  
 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]项目系统提供了支持访问生成的类和类型通过临时的可移植可执行文件 (临时 PEs)。 自定义工具生成的任何文件可以编译到临时程序集，以便可以从这些程序集加载类型，并将其公开给设计器。 每个自定义工具的输出会编译成单独的临时 PE，并是成功还是失败的此临时编译仅取决于可以编译生成的文件。 即使的项目可能不生成作为一个整体，单个临时 PEs 可能仍可供设计器。  
  
 项目系统提供完全支持跟踪以更改到输出文件的自定义工具，前提是这些更改是运行自定义工具的结果。 每次运行自定义工具时，将生成新的临时 PE，并相应的通知发送到设计器。  
  
> [!NOTE]
>  因为临时程序可执行文件的生成文件发生在后台，所以如果编译失败未向用户不报告任何错误。  
  
 自定义工具，它们利用临时 PE 支持必须遵循以下规则：  
  
-   `GeneratesDesignTimeSource`必须设置为 1 的注册表中。  
  
     没有程序可执行文件编译将无此设置的位置。  
  
-   生成的代码必须是全局的项目设置为相同的语言。  
  
     临时 PE 编译而不考虑自定义工具报告中的请求扩展作为<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>假设`GeneratesDesignTimeSource`在注册表中设置为 1。 该扩展不需要为.vb、.cs 或.jsl;它可以是任何扩展。  
  
-   由自定义工具生成的代码必须是有效的并且在其自己使用仅集的引用项目中存在时，它必须编译<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>执行完毕。  
  
     编译临时 PE 后，向编译器提供的唯一源文件是自定义工具输出。 因此，使用临时 PE 的自定义工具必须生成可以独立于项目中的其他文件编译的输出文件。  
  
## <a name="see-also"></a>另请参阅  
 [简介 BuildManager 对象](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [实现单个文件生成器](../../extensibility/internals/implementing-single-file-generators.md)   
 [注册单个文件生成器](../../extensibility/internals/registering-single-file-generators.md)