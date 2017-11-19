---
title: "实现单个文件生成器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9894666dd435dcaa110ba8af8307d7e942119bee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-single-file-generators"></a>实现单个文件生成器
自定义工具-有时称为单个文件生成器 — 可用于扩展[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]项目中的系统[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 自定义工具是实现的 COM 组件<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>接口。 使用此接口，一个自定义工具会将单个输入的文件都转换为单个输出文件。 转换的结果可能是源代码或任何其他输出的非常有用。 自定义工具生成的代码文件的两个示例是在可视化设计器和生成使用 Web 服务描述语言 (WSDL) 文件中的更改的响应中生成代码。  
  
 当加载自定义工具，或保存输入的文件时，项目系统调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>方法，并将传递对引用<xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>回调接口，凭此工具可以向用户报告其进度。  
  
 自定义工具生成的输出文件添加到输入文件的依赖项目。 项目系统将自动确定的基于自定义工具的实现返回的字符串的输出文件的名称<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>。  
  
 必须实现一个自定义工具<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>接口。 自定义工具的支持 （可选）<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>接口以从输入文件以外的源中检索信息。 在任何情况下，你可以使用自定义工具之前，你必须注册它与系统或在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本地注册表。 注册自定义工具的详细信息，请参阅[注册单个文件生成器](../../extensibility/internals/registering-single-file-generators.md)。  
  
## <a name="see-also"></a>另请参阅  
 [向可视化设计器公开类型](../../extensibility/internals/exposing-types-to-visual-designers.md)