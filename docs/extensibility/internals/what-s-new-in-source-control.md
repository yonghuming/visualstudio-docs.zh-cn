---
title: "在源代码管理中的新增功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "什么是新的 [Visual Studio SDK]，源代码管理"
  - "源代码管理 [Visual Studio SDK]，新增功能"
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# 在源代码管理中的新增功能
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 通过实现源控件提供了一种更深入地集成到源代码管理解决方案 VSPackage。  本节描述源代码管理 Vspackage 功能并提供实现步骤概述。  
  
## 源代码管理 VSPackage  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支持源代码管理解决方案的两种类型。  在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的所有版本中，您仍可以集成源代码管理插件基于 API 的插件。  还可以创建提供一个集成， [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 路径适用于源代码管理解决方案需要高级优雅和自治权的源代码管理的 VSPackage。  
  
 VSPackage 中添加几乎任何功能。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  源代码管理 VSPackage 为 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供完整源代码管理功能，从 UI 对用户显示为源代码管理系统的后端通信。  
  
 实现任何源代码管理 VSPackage 不需要任何 “或”方法。  源代码管理 VSPackage 的创建者在实现必须投资大量工作量很多源控制接口以及新 UI 元素 \(对话框、菜单和工具栏\) 复盖整个源代码管理功能，以及接口需要任何包成功与集成 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 以下步骤来提供了一个一般概述所需的实现源代码管理包。  有关详细信息，请参见[创建源控件 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。  
  
1.  创建提供专用源代码管理服务的 VSPackage。  
  
2.  实现接口 \(例如由 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供的源控件相关的服务中 \(， <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> 接口\)。  
  
3.  注册源代码管理 VSPackage。  
  
4.  实现包括菜单项、对话框、工具栏和上下文菜单的所有源代码管理用户界面，。  
  
5.  ，它是活动的，且必须由 VSPackage 时，处理所有源代码管理相关的事件传递给数据源控件 VSackage。  
  
6.  源代码管理 VSPackage 必须侦听事件 \(如实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> 接口的控件并跟踪项目文档 \(TPD\)事件 \(由 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 实现的接口\) 并执行必要的操作。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [概述](../../extensibility/internals/source-control-integration-overview.md)   
 [创建源控件 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)