---
title: "自定义工具 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c198065c72f1e6eaa0722de562abe6079f88aa1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="custom-tools"></a>自定义工具
*自定义工具*让你可以将工具与项目中的项相关联并运行该工具，每当保存该文件。 某些自定义工具，有时称为*单个文件生成器*，经常用于实现转换器生成代码，从数据，反之亦然。 例如，单个文件生成器创建[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]源代码外.settings 和.resx 文件。 生成的源代码提供对.settings 和.resx 文件中的数据的强类型访问。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]项目类型支持自定义工具;[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]项目类型不这样做。 您自己的项目类型还可以支持自定义工具。  
  
 自定义工具是实现的已注册的组件`IVsSingleFileGenerator`接口。  
  
 与之关联的自定义工具`ProjectItem`接口对象，就像设计器和编辑器一样。 自定义工具将表示的文件`ProjectItem`作为输入，并将其文件名由一个新文件写入`DefaultExtension`方法。  
  
## <a name="in-this-section"></a>本节内容  
 [实现单个文件生成器](../../extensibility/internals/implementing-single-file-generators.md)  
 介绍如何使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>接口才能实现一个自定义工具。  
  
 [注册单个文件生成器](../../extensibility/internals/registering-single-file-generators.md)  
 自定义工具中提供的所有注册表条目的说明。  
  
 [向可视化设计器公开类型](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 说明如何项目系统支持对访问生成类和类型的可视化设计器通过提供临时的可移植可执行 (PE) 文件。  
  
 [保留项目项的属性](../../extensibility/persisting-the-property-of-a-project-item.md)  
 演示如何来持久保存项目项属性，如项目文件中，在源文件的作者。  
  
## <a name="reference"></a>参考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 提供有关的详细信息<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>，这将单个输入的文件转换为可以编译或添加到项目的单个输出文件。  
  
 <xref:EnvDTE.ProjectItem>  
 说明`ProjectItem`接口，它表示项目中的项。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 提供有关的详细信息`DefaultExtension`方法，检索赋予输出文件的名称的文件扩展名。  
  
## <a name="related-sections"></a>相关章节  
 [扩展项目](../../extensibility/extending-projects.md)  
 介绍如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]项目和解决方案来组织代码文件和资源文件，以及如何实现源代码管理。