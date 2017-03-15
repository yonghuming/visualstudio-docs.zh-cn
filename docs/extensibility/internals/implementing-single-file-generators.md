---
title: "实现单文件生成器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "实现的自定义工具"
  - "项目 [Visual Studio SDK]，可扩展性"
  - "项目 [Visual Studio SDK]，管理自定义工具"
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 实现单文件生成器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

自定义工具 \(有时称为单文件生成器 —可用于扩展在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 和 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 项目系统。  自定义工具是实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 接口的 COM 组件。  使用此接口，自定义工具转换一个输入文件转换为单个输出文件。  该转换的结果可能是源代码，也很有用的其他输出。  自定义工具生成的代码文件中的两个示例是使用 web 服务描述语言 \(wsdl\) 生成的代码生成响应在可视化设计器中的更改和文件 \(WSDL\)。  
  
 当自定义工具加载时，或者输入文件保存，项目系统调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 方法，并传递对 <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> 回调接口，该接口，供工具可以其用户报告进度。  
  
 自定义工具生成的输出文件添加到项目与输入文件的依赖项。  项目系统基于 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>的自定义工具的实现返回的字符串自动确定输出文件的名称，。  
  
 自定义工具必须实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 接口。  或者，除了输入文件之外，自定义工具支持 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> 接口从数据源中检索信息。  在任何情况下，，然后才能使用自定义工具之前，必须向系统注册该或在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 本地注册表。  有关注册自定义工具的更多信息，请参见 [注册的单文件生成器](../../extensibility/internals/registering-single-file-generators.md)。  
  
## 请参阅  
 [确定项目的默认命名空间](../../misc/determining-the-default-namespace-of-a-project.md)   
 [公开到可视化设计器的类型](../../extensibility/internals/exposing-types-to-visual-designers.md)