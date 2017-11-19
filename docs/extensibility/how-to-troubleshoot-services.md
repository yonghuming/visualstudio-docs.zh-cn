---
title: "如何： 解决服务问题 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c241b80430fd02a649efab7f8a65498e606d2804
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-troubleshoot-services"></a>如何： 解决服务问题
有几个常见的问题，当你尝试将获得的服务时可能发生：  
  
-   服务未注册[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
-   在请求服务时由接口类型而不是服务类型。  
  
-   位置不正确 VSPackage 请求该服务。  
  
-   使用错误的服务提供程序。  
  
 如果请求的服务无法获取，则会调用<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>，则返回 null。 你应始终测试存在 null 请求服务后：  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>若要解决服务问题  
  
1.  检查系统注册表，以查看服务是否已正确注册。 有关详细信息，请参阅[如何： 提供服务](../extensibility/how-to-provide-a-service.md)。  
  
     下面的.reg 文件片断演示可能注册 SVsTextManager 服务的方式：  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     在上面的示例中，版本号是版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，例如 12.0 或 14.0，注册表项 {F5E7E71D-1401-11d1-883B-0000F87579D2} 是服务、 SVsTextManager 和默认值 {的服务标识符 (SID)F5E7E720-1401-11d1-883B-0000F87579D2} 是包的文本管理器 VSPackage，它提供服务的 GUID。  
  
2.  调用 GetService 时，请使用服务类型而不是接口类型。 请求服务时[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，<xref:Microsoft.VisualStudio.Shell.Package>提取类型的 GUID。 如果满足下列条件，将不会找到服务：  
  
    1.  接口类型而不是服务类型传递给 GetService。  
  
    2.  未 GUID 显式分配给的接口。 因此，系统会创建为根据需要的对象的默认 GUID。  
  
3.  请确保已放置 VSPackage 请求该服务。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]构造它之后和调用之前站点 VSPackage <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>。  
  
     如果你需要一种服务的 VSPackage 构造函数中有代码，则将其移到的 Initialize 方法。  
  
4.  请确保你正在使用正确的服务提供程序。  
  
     并非所有的服务提供商相似。 服务提供商，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]传递到工具窗口不同于将其传递到 VSPackage。 工具窗口服务提供程序就会了解有关<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>，但不知道<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>。 你可以调用<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>若要在工具窗口中获取的 VSPackage 服务提供程序。  
  
     如果工具窗口托管的用户控件或任何其他控件容器，容器将被放置 Windows 组件模型，并且将不具有访问任何[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]服务。 你可以调用<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>若要获取的 VSPackage 服务提供程序中的控件容器。  
  
## <a name="see-also"></a>另请参阅  
 [可用服务列表](../extensibility/internals/list-of-available-services.md)   
 [使用和提供服务](../extensibility/using-and-providing-services.md)   
 [服务基础知识](../extensibility/internals/service-essentials.md)