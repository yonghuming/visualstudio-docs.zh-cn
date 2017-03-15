---
title: "解决方案配置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "解决方案配置"
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 解决方案配置
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

解决方案配置存储解决方案级别的属性。 它们指示的行为 **Start** \(F5\) 密钥和 **Build** 命令。 默认情况下，这些命令将生成并启动调试配置。 解决方案配置的上下文中执行这两个命令。 这意味着用户可以启动和任何活动解决方案配置通过设置生成期望 F5。 环境设计为生成和运行时达到最优的解决方案，而不是项目。  
  
 标准的 Visual Studio 工具栏包含开始按钮和解决方案配置下拉列表右侧的开始按钮。 此列表使用户能够选择时按下 F5 启动的配置、 创建他们自己的解决方案配置或编辑现有的配置。  
  
> [!NOTE]
>  没有可扩展性接口来创建或编辑解决方案配置。 必须使用 `DTE.SolutionBuilder`。 但是，有一些用于管理解决方案生成的可扩展 Api。 有关详细信息，请参阅<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>。  
  
 下面是如何实现您的项目类型支持的解决方案配置:  
  
-   Project  
  
     显示当前解决方案中找到的项目的名称。  
  
-   配置  
  
     若要提供您的项目类型所支持的配置列表并显示在属性页中，实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>。  
  
     配置列显示在此解决方案配置中，生成的项目配置的名称，并列出所有的项目配置，当您单击箭头按钮。 环境调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> 方法来填写此列表。 如果 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> 方法指示项目支持配置编辑，新建或编辑的选择也会显示在配置标题下。 这些选择的每个启动调用的方法的对话框 `IVsCfgProvider2` 界面以编辑项目的配置。  
  
     如果项目不支持的配置，则配置列显示无且被禁用。  
  
-   平台  
  
     显示选定的项目配置生成，并单击箭头按钮时列出所有可用的平台的项目的平台。 环境调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> 方法来填写此列表。 如果 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> 方法指示项目支持的平台编辑，新建或编辑选择也会显示在平台标题下。 这些选择的每个启动调用的对话框 `IVsCfgProvider2` 方法来编辑项目的可用的平台。  
  
     如果项目不支持的平台，该项目的平台列显示无且被禁用。  
  
-   生成  
  
     指定在项目生成由当前的解决方案配置。 尽管它们所包含的任何项目依赖项调用解决方案级生成命令时不生成未选定的项目。 未选定要生成的项目仍包括在调试、 运行、 打包和部署解决方案中。  
  
-   部署  
  
     指定选定的解决方案生成配置使用启动或部署命令时将部署该项目。 此字段的复选框将只有一个项目支持通过实现部署 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 接口及其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 对象。  
  
 一旦添加新的解决方案配置，用户可以选择它从标准工具栏来构建和\/或启动该配置的解决方案配置下拉列表框。  
  
## 请参阅  
 [管理配置选项](../../extensibility/internals/managing-configuration-options.md)   
 [生成的项目配置](../../extensibility/internals/project-configuration-for-building.md)   
 [项目配置对象](../../extensibility/internals/project-configuration-object.md)