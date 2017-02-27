---
title: "自定义工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vspackage，自定义工具"
  - "工具 [Visual Studio]，自定义"
  - "自定义工具"
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# 自定义工具
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

*自定义工具* 使您可以将工具与项目中的项并运行该工具，每当保存文件。  某些自定义工具，有时称为 *单文件生成器*，通常用于实现从生成数据的代码反之亦然的转换器。  例如，单文件生成器创建 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 源代码在 .settings 和 .resx 文件外部。  生成的源代码提供对数据的强类型访问在 .settings 和 .resx 文件。  [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 项类型支持自定义工具; [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项类型不。  拥有项目类型可能还支持自定义工具。  
  
 自定义工具是实现 `IVsSingleFileGenerator` 接口的注册的元素。  
  
 自定义工具与 `ProjectItem` 界面对象，并与设计器和编辑器。  自定义工具以 `ProjectItem` 表示的文件，因为输入和写入 `DefaultExtension` 方法提供文件名的新文件。  
  
## 本节内容  
 [实现单文件生成器](../../extensibility/internals/implementing-single-file-generators.md)  
 描述如何使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 接口实现自定义工具。  
  
 [确定项目的默认命名空间](../../misc/determining-the-default-namespace-of-a-project.md)  
 描述如何确定基于语言的正确命名空间使用。  
  
 [注册的单文件生成器](../../extensibility/internals/registering-single-file-generators.md)  
 为自定义工具的任何注册表项的标题。  
  
 [公开到可视化设计器的类型](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 解释项目系统如何提供可视化设计器支持访问生成的类和类型通过临时可移植可执行 \(pe\) 文件 \(PE\)。  
  
 [保存项目项的属性](../../extensibility/persisting-the-property-of-a-project-item.md)  
 在项目文件中显示如何保持一个项目项属性，如源文件的作者，。  
  
## 参考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 提供有关 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>的详细信息，转换一个输入文件转换为单个输出文件可编译或添加到项目中。  
  
 <xref:EnvDTE.ProjectItem>  
 解释 `ProjectItem` 接口，表示项目中的项。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 提供有关 `DefaultExtension` 方法的详细信息，检索文件扩展名指定输出文件名。  
  
## 相关章节  
 [扩展项目](../../extensibility/extending-projects.md)  
 描述如何使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 项目和解决方案组织代码文件和资源文件以及如何实现数据源控件。