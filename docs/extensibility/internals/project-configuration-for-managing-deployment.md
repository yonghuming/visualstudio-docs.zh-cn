---
title: "用于管理部署的项目配置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目配置，部署进行管理"
  - "项目 [Visual Studio SDK]，部署进行管理的配置"
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 用于管理部署的项目配置
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

部署是实际移动输出项操作从生成过程到调试和安装的预期位置。  例如， Web 应用程序在本地计算机在服务器可能会生成然后放置。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支持两种项目在部署可包括:  
  
-   部署的主题处理。  
  
-   部署管理器的过程。  
  
 在解决方案中部署之前，必须先添加部署项目配置部署选项。  如果部署项目尚不存在，则会询问您是否希望创建一个，当选择 **部署解决方案** 从 **生成** 菜单或右击解决方案时。  单击 **是** 打开选定的 **远程部署向导** 项目的 **添加新项目** 对话框。  
  
 远程部署向导要求您应用程序的类型 \(windows 或 Web\)，项目输出组中，选中要包含的所有其他文件和要部署的远程计算机。  向导的最后一页显示选定选项的摘要。  
  
 作为部署的主题的项目处理生成必须移动到备用环境的输出项。  这些输出项称为 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 接口的参数，主要用途，如果允许项添加到组输出。  有关 `IVsProjectCfg2`的实现的相关更多信息，请参见 [输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)。  
  
 部署项目，管理部署过程，以启用 " 部署命令并响应，则此命令时。  部署项目实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 接口执行部署，并调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> 接口报告部署状态事件。  
  
 配置可以指定影响其生成或部署操作的依赖项。  生成或部署依赖项是必须生成或部署的项目中，在配置生成或部署前后。  创建了项目之间的依赖项描述用于 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> 接口和部署依赖项和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> 接口。  有关更多信息，请参见 [生成的项目配置](../../extensibility/internals/project-configuration-for-building.md)。  
  
## 请参阅  
 [管理配置选项](../../extensibility/internals/managing-configuration-options.md)   
 [生成的项目配置](../../extensibility/internals/project-configuration-for-building.md)   
 [输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)