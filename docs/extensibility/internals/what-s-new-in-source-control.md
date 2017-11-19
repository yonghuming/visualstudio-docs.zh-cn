---
title: "什么 &#39; s 源代码管理中的新增功能 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 946a3c9fb7d3f0ccd6a90383f6ca22d91c0009a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="what39s-new-in-source-control"></a>什么 &#39; s 源代码管理中的新增功能
在[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]你可以通过实现 VSPackage 的源控件提供深入地集成的源代码管理解决方案。 此部分描述源控件 Vspackage 的功能，并提供的实现步骤概述。  
  
## <a name="the-source-control-vspackage"></a>源控件 VSPackage  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支持两种类型的源控制解决方案。 在所有版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，仍可以将集成基于源控制插件 API 的插件。 你还可以创建用于源代码管理提供深层集成 VSPackage[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]适合需要的复杂程度和自主性高级别的源控制解决方案的路径。  
  
 VSPackage 可以添加几乎任何类型的功能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 源代码管理 VSPackage 提供的完整源代码管理功能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，从显示到与源代码管理系统的后端通信的用户的 UI。  
  
 实现源代码管理 VSPackage 需要使用"所有或执行任何操作"的策略。 源控件 VSPackage 的创建者必须投资占用大量的精力实现大量的源控制接口和新的 UI 元素 （对话框、 菜单和工具栏） 以涵盖整个源的控件功能，以及接口集成所需的任何包成功与[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 以下步骤为提供所需的实现源代码管理包的一般概述。 有关详细信息，请参阅[创建源控件 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。  
  
1.  创建 VSPackage proffers 私有源控制服务。  
  
2.  在通过提供的源控件相关服务实现接口[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](例如，<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>接口)。  
  
3.  注册您的源代码管理 VSPackage。  
  
4.  实现所有源代码管理 UI，包括菜单项、 对话框、 工具栏和上下文菜单。  
  
5.  所有源控件相关的事件都传递到源代码管理 VSackage 时它处于活动状态，并且必须由你的 VSPackage。  
  
6.  您的源代码管理 VSPackage 必须侦听事件如实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>接口以及跟踪项目文档 (TPD) 事件 (的实施方式<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>接口) 并采取必要措施。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [概述](../../extensibility/internals/source-control-integration-overview.md)   
 [创建源代码管理 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)