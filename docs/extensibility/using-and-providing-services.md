---
title: "使用和提供服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: "41"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e28b66dea8440c969926abd3892739f4e041b064
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-and-providing-services"></a>使用和提供服务
服务是两个 Vspackage 之间的协定。 一个 VSPackage 提供一组特定的接口，另一个 VSPackage 来使用。 例如，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]提供<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>服务到任何 VSPackage 它加载。 此服务提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>接口，可用来向活动日志中写入。 有关详细信息，请参阅[如何： 使用活动日志](../extensibility/how-to-use-the-activity-log.md)。  
  
 Vspackage 可以提供自己的通过使用服务<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>接口...  
  
 Visual Studio 提供重要服务，如下所示：  
  
|IDE 服务|描述|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|提供访问 IDE 的基本功能、 Vspackage，与注册表服务处理。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本窗口化和 UI 相关的功能，在 IDE 中，如创建工具和文档窗口的功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供基本的解决方案相关的功能，如能够枚举项目、 创建新项目，和监视项目进行的更改。|  
  
## <a name="in-this-section"></a>本节内容  
 [服务基础知识](../extensibility/internals/service-essentials.md)  
 提供 Visual Studio 服务的重要元素。  
  
 [如何：获取服务](../extensibility/how-to-get-a-service.md)  
 讨论如何请求 （使用） 服务。  
  
 [如何：提供服务](../extensibility/how-to-provide-a-service.md)  
 讨论如何提供服务。  
  
 [如何：提供异步 Visual Studio 服务](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 讨论如何提供异步的服务。  
  
 [如何：进行服务的故障排除](../extensibility/how-to-troubleshoot-services.md)  
 讨论常见的问题并提供给他们的解决方案。  
  
## <a name="related-sections"></a>相关章节  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)