---
title: "解决方案配置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b9009a4adab2420a796b3011175ef37fac9bfcb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="solution-configuration"></a>解决方案配置
解决方案配置存储解决方案级别的属性。 它们指示的行为**启动**(f5) 和**生成**命令。 默认情况下，这些命令将生成并启动调试配置。 解决方案配置的上下文中执行这两个命令。 这意味着用户可以启动和生成通过设置配置任何活动解决方案中期望 F5。 环境旨在针对解决方案而不是项目到构建和运行时进行优化。  
  
 标准的 Visual Studio 工具栏包含一个开始按钮和解决方案配置开始按钮右侧的下拉列表。 此列表允许用户选择要在按下 F5 时启动的配置、 创建其自己的解决方案配置，或编辑现有配置。  
  
> [!NOTE]
>  没有可扩展性接口来创建或编辑解决方案配置。 必须使用`DTE.SolutionBuilder`。 但是，用于管理解决方案生成有扩展性 Api。 有关更多信息，请参见<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>。  
  
 下面是如何实现支持你的项目类型的解决方案配置：  
  
-   Project  
  
     显示当前解决方案中找到的项目的名称。  
  
-   配置  
  
     若要提供的支持你的项目类型的配置列表和显示在属性页中，实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>。  
  
     配置列显示在此解决方案配置中，生成的项目配置的名称，并单击箭头按钮时列出所有项目的配置。 环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A>填写此列表的方法。 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>方法指示项目支持配置编辑，新建或编辑选择也会显示配置标题下。 每个这些选择启动调用的方法的对话框`IVsCfgProvider2`界面以编辑项目的配置。  
  
     如果项目不支持的配置，配置列显示无和为禁用。  
  
-   平台  
  
     显示选定的项目配置生成，并单击箭头按钮时列出的所有可用项目平台的平台。 环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A>填写此列表的方法。 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>方法指示项目支持平台编辑，新建或编辑选择也会显示平台标题下。 每个这些选择启动调用的对话框`IVsCfgProvider2`方法编辑项目的可用平台。  
  
     如果项目不支持的平台，该项目的平台列显示无和为禁用。  
  
-   生成  
  
     指定由当前的解决方案配置生成项目。 尽管它们所包含的任何项目依赖项调用的解决方案级生成命令时不生成未选定的项目。 未选定要生成的项目仍包含在调试、 运行、 打包和部署解决方案中。  
  
-   部署  
  
     指定的开始或部署命令使用选择的解决方案生成配置时，将部署项目。 此字段复选框将只有一个项目支持通过实现部署<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>接口其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>对象。  
  
 一旦添加新的解决方案配置，用户可以选择它从要生成和/或启动该配置标准工具栏上的解决方案配置下拉列表框。  
  
## <a name="see-also"></a>另请参阅  
 [管理配置选项](../../extensibility/internals/managing-configuration-options.md)   
 [生成的项目配置](../../extensibility/internals/project-configuration-for-building.md)   
 [项目配置对象](../../extensibility/internals/project-configuration-object.md)