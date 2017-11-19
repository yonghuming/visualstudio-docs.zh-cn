---
title: "源控件 VSPackage 体系结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80153e271fed6a7fab49e00c8124f1ede7613bfa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-vspackage-architecture"></a>源控件 VSPackage 体系结构
源代码管理包是使用 VSPackage 服务[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 提供。 反过来，源代码管理包提供其功能作为源控件服务。 此外，源代码管理包是一个更通用的替代方案，比了源代码管理集成到源代码管理插件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 源代码管理插件实现源控制插件 API 遵守严格的协定。 例如，对于插件无法替换默认[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]用户界面 (UI)。 此外，源控制插件 API 不会启用插件来实现其自己的源控件模型。 源代码管理包，但是，克服了这两个这些限制。 源代码管理包可以完全控制的源控件体验[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]用户。 此外，源代码管理包可以使用其自己的源控件模型和逻辑，并且它可以定义源控件相关的用户的所有接口。  
  
## <a name="source-control-package-components"></a>源代码管理包组件  
 体系结构关系图中中, 所示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]组件名为源存根 （stub） 是集成的源代码管理包的 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 源存根 （stub） 处理以下任务。  
  
-   提供常见用户界面，所需的源代码管理包注册。  
  
-   加载源代码管理包。  
  
-   将源代码管理包设置为活动/非活动。  
  
 源存根 （stub） 查找源代码管理包的活动服务，并将路由从 IDE 到该包的所有传入服务调用。  
  
 源代码管理适配器包是一个特殊的源控件包[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供。 此包是用于支持源控件插件基于源控件插件 API 的核心组件。 源代码管理插件时插件的活动，源存根 （stub） 会将其事件发送到源控件适配器包。 反过来，源代码管理适配器包使用源控件插件 API 与源代码管理插件进行通信，并提供默认值是很常见的所有源控件插件的 UI。  
  
 活动的包的源代码管理包时，另一方面，源存根 （stub） 直接使用与通信包[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]源代码管理包的接口。 源代码管理包是负责承载其自己的源代码管理 UI。  
  
 ![源代码管理体系结构图](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 源代码管理包，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]未提供源控件代码或集成的 API。 中所述的方法与此形成对比[创建源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)源代码管理插件不得不实现一组严格的函数和回调的位置。  
  
 如任何 VSPackage，源代码管理包是可以通过使用创建的 COM 对象`CoCreateInstance`。 VSPackage 使其可供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通过实现 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。 VSPackage 创建实例后，接收一个指针，站点和<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>提供对可用的服务和在 IDE 中的接口的 VSPackage 访问接口。  
  
 编写基于 VSPackage 的源代码管理包需要更高级编程的专业知识不仅仅编写基于源控制插件 API 的插件。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [入门](../../extensibility/internals/getting-started-with-source-control-vspackages.md)