---
title: "VSPackage 结构 (源控件 VSPackage) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f8422e4333c1f1ccffc928ce9a43e4afa53cc7a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 结构 (源控件 VSPackage)
源控件包 SDK 提供用于创建 VSPackage 的准则允许源控件实施者，要将他或她源控件功能与集成[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]环境。 VSPackage 是一个 COM 组件，通常按需通过加载[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 基于由其注册表项中的包播发的服务。 每个 VSPackage 必须实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。 VSPackage 通常使用提供的服务[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 和 proffers 自己的某些服务。  
  
 VSPackage 声明其菜单项，并建立通过.vsct 文件的默认项状态。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 显示的菜单项处于此状态直到加载 VSPackage。 随后，VSPackage 的实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>调用方法来启用或禁用菜单项。  
  
## <a name="source-control-package-characteristics"></a>源控件包特征  
 VSPackage 紧密地集成到一个源控件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 VSPackage 语义包括：  
  
-   接口实现的 VSPackage (`IVsPackage`接口)  
  
-   UI 命令实现 (.vsct 文件和实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口)  
  
-   使用 VSPackage 注册[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 源代码管理 VSPackage 必须与这些其他[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]实体：  
  
-   项目  
  
-   编辑器  
  
-   解决方案  
  
-   Windows  
  
-   正在运行的文档表  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>可能使用的 visual Studio 环境服务  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider 服务  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP 接口实现和调用  
 源代码管理包是 VSPackage，并且因此它可以直接与注册的其他 Vspackage 交互[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 为了提供全套源代码管理功能，源代码管理 VSPackage 可以处理由项目或 shell 提供的接口。  
  
 在每个项目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必须实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>识别为中的项目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。 但是，此接口不专用足够用于源代码管理。 预计会在源下的项目控制实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>。 若要查询其内容的项目，并将该标志符号和绑定信息 （所需的信息的服务器位置和项目下的磁盘位置之间建立连接，使用此接口由源代码管理 VSPackage源代码管理）。  
  
 VSPackage 实现的源控件<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>，这反过来允许项目，以便将其本身注册为源控件和检索其状态标志符号。  
  
 有关源代码管理 VSPackage 必须考虑的接口的完整列表，请参阅[相关服务和界面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)。  
  
## <a name="see-also"></a>另请参阅  
 [设计元素](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [相关的服务和接口](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)