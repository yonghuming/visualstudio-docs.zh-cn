---
title: "源控件 VSPackage 体系结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理包，体系结构"
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 源控件 VSPackage 体系结构
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

源代码管理包是使用服务 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 提供的 VSPackage。  反过来，源代码管理包提供其功能作为源代码管理服务。  此外，源代码管理包与集成的源代码管理的源管理插件更通用的替代项。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 实现源代码管理插件 API 的源代码管理插件遵循严格的协定。  例如，插件不能替换默认 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 用户界面 \(UI\)。  此外，源代码管理插件 API 不会使插件实现自己的数据源控件模型。  源代码管理包，但是，解决这两种限制。  源代码管理包对 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 用户的源代码管理体验的完全控制。  此外，源代码管理包可以使用自己的数据源控件模型和逻辑，因此，它可以定义所有源代码管理相关的用户界面。  
  
## 源代码管理包组件  
 根据体系结构示意图所示，名为源代码管理存根的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 元素是集成具有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的源控件包的 VSPackage。  
  
 源代码管理存根 \(stub\) 处理以下任务。  
  
-   提供了源代码管理包注册所需的公共 UI。  
  
-   加载源控件包。  
  
-   设置源代码管理包为无效\/非活动。  
  
 源代码管理存根查找源控件包的有效的服务并将所有传入从 IDE 服务请求绑定到该包。  
  
 源控件适配器包是 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供的特定源代码管理包。  此包是支持的基于源代码管理插件 API 的源代码管理插件主要组件。  在源代码管理插件是有效的插件时，源代码管理存根将其事件添加到源控件适配器包。  然后，数据源控件适配器包与源代码管理插件的通信是通过使用源代码管理插件 API 并提供对所有源代码管理插件共有的默认 UI。  
  
 在源代码管理包是有效的包，另一方面中使用 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 源代码管理包，接口，源代码管理存根与包直接通信。  源代码管理包在其自己的源代码管理负责 UI。  
  
 ![源代码管理体系结构图](~/extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 向源代码管理包， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 不提供源代码管理代码或 API 集成的。  将此与源代码管理插件必须实现严格的功能集和回调的 [创建了源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md) 概述的方法。  
  
 与所有 VSPackage，源代码管理包是使用 `CoCreateInstance`，则可以创建的 COM 对象。  VSPackage 排列自身可用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 通过实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。  当创建实例后， VSPackage 接收站点指针和提供对可用的服务和接口的 VSPackage 访问在 IDE 中 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 接口。  
  
 编写基于 VSPackage 的源代码管理包与编写源代码管理插件基于 API 的插件需要更高级编程的专业知识。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [入门](../../extensibility/internals/getting-started-with-source-control-vspackages.md)