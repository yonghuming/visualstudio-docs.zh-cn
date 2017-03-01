---
title: "使用并提供服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 41
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fb380330420d6256190ade75e0afe89f8cbda303
ms.lasthandoff: 02/22/2017

---
# <a name="using-and-providing-services"></a>使用并提供服务
服务是两个 VSPackages 迁移之间的协定。 一个 VSPackage 提供了一组特定的另一个的 VSPackage，若要使用的接口。 例如，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]提供<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>服务于任何 VSPackage 它加载。</xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 此服务提供的<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>界面，可用于写入活动日志。</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 有关详细信息，请参阅[如何︰ 使用活动日志](../extensibility/how-to-use-the-activity-log.md)。  
  
 VSPackages 迁移可以提供自己的服务通过使用<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>接口...</xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>  
  
 Visual Studio 提供重要服务，如下所示︰  
  
|IDE 服务|描述|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|提供了访问 IDE 的基本功能、 VSPackages 迁移，与注册表服务处理。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供了基本的窗口和在 IDE 中，例如创建工具和文档窗口的功能与 UI 相关的功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution></xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供基本与相关的解决方案的功能，如能够枚举项目、 创建新项目，以及监视项目进行的更改。|  
  
## <a name="in-this-section"></a>本节内容  
 [服务基础知识](../extensibility/internals/service-essentials.md)  
 显示 Visual Studio 服务的重要元素。  
  
 [如何︰ 获取服务](../extensibility/how-to-get-a-service.md)  
 讨论如何请求 （使用） 服务。  
  
 [如何︰ 提供的服务](../extensibility/how-to-provide-a-service.md)  
 讨论如何提供服务。  
  
 [如何︰ 提供异步 Visual Studio 服务](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 讨论如何提供异步服务。  
  
 [如何︰ 解决服务疑难问题](../extensibility/how-to-troubleshoot-services.md)  
 讨论常见的问题并提供了对它们的解决方案。  
  
## <a name="related-sections"></a>相关章节  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
