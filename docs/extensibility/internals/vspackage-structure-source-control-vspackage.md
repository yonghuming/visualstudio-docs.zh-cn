---
title: "VSPackage 结构 (源控制 VSPackage) | Microsoft Docs"
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
  - "VSPackages 迁移结构"
  - "源代码管理包，VSPackage 概述"
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# VSPackage 结构 (源控制 VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

源控件包 SDK 提供了关于如何创建 VSPackage 指导允许源控件实施者，可以将集成他或她的源代码管理功能与 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 环境。 VSPackage 是一个 COM 组件，通常可以立即加载由点播 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 集成的开发环境 \(IDE\) 基于在其注册表项中的包播发的服务。 每个 VSPackage 必须实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。 VSPackage 通常只占用所提供的服务 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 和 proffers 某些服务。  
  
 VSPackage 声明其菜单项，并建立通过.vsct 文件的默认项状态。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 的菜单项将在显示此状态直到加载 VSPackage。 随后，VSPackage 的实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 调用方法来启用或禁用菜单项。  
  
## 源控件封装特性  
 VSPackage 紧密地集成到源代码管理 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 VSPackage 语义包括︰  
  
-   接口实现的 VSPackage \( `IVsPackage` 接口\)  
  
-   UI 命令实现 \(.vsct 文件和实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口\)  
  
-   注册与 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 源代码管理 VSPackage 必须与服务器通信这些其他 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 实体︰  
  
-   项目  
  
-   编辑器  
  
-   解决方案  
  
-   Windows  
  
-   正在运行的 document 表  
  
### 也可能使用的 visual Studio 环境服务  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider 服务  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### VSIP 接口实现和调用  
 源代码管理包是 VSPackage，因此它可直接与注册的其他 Vspackage 交互 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 为了提供全面的源代码管理功能，源代码管理 VSPackage 可以处理由项目或外壳中提供的接口。  
  
 每个项目中的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必须实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> 若要识别中的项目为 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。 但是，此接口不专用化足够用于源代码管理。 用户期望可在源下的项目控制实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>。 若要查询其内容的项目，并提供该标志符号和绑定信息 （所需的服务器位置和磁盘上的受源代码管理的项目位置之间建立连接的信息），将由源控件 VSPackage 使用此接口。  
  
 VSPackage 实现的源代码管理 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, ，这样便可以让项目，以便进行源代码管理中注册自身和检索其状态标志符号。  
  
 源代码管理 VSPackage 必须考虑的接口的完整列表，请参阅 [相关的服务和接口](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)。  
  
## 请参阅  
 [设计元素](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [相关的服务和接口](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)