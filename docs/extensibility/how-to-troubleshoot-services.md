---
title: "如何: 解决服务疑难问题 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "服务，故障排除"
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何: 解决服务疑难问题
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有几个 when you try to 获取服务可以发生的常见问题:  
  
-   该服务未注册 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
-   在请求服务时由接口类型而不是服务类型。  
  
-   位置不正确 VSPackage 请求该服务。  
  
-   使用错误的服务提供程序。  
  
 如果请求的服务无法获得，则会调用 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> ，则返回 null。 您应该始终测试存在 null 请求服务之后:  
  
```c#  
IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog; if (log == null) return;  
```  
  
### 若要解决服务问题  
  
1.  检查系统注册表，以查看是否已正确注册该服务。 有关详细信息，请参阅[注册服务](../misc/registering-services.md)。  
  
     下面的.reg 文件片断演示可能注册 SVsTextManager 服务的方式:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
    ```  
  
     在上面的示例中，版本号是版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，如 12.0 或 14.0，键 {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} 是 SVsTextManager，服务的服务标识符 \(SID\)，默认值 {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} 是包的文本管理器 VSPackage，它提供服务的 GUID。  
  
2.  当您调用 GetService 时使用的服务类型而不是接口类型。 请求的一项服务时 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，<xref:Microsoft.VisualStudio.Shell.Package> 提取从类型的 GUID。 如果满足下列条件，将不会找到一种服务:  
  
    1.  接口类型而不是服务类型传递给 GetService。  
  
    2.  没有 GUID 显式分配给的接口。 因此，系统会创建为所需的对象的默认 GUID。  
  
3.  请确保已放置 VSPackage 请求该服务。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 构建该信息之后，然后才能调用站点 VSPackage <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>。  
  
     如果您需要一种服务的 VSPackage 构造函数中的代码，则将其移动到的初始化方法。  
  
4.  请确保您正在使用正确的服务提供程序。  
  
     并非所有服务提供程序都是相同的。 服务提供商， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将传递到工具窗口不同于将其传递到 VSPackage。 工具窗口服务提供商知道 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, ，但并不了解 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>。 您可以调用 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 工具窗口中获取的 VSPackage 服务提供程序。  
  
     如果一个工具窗口承载用户控件或任何其他控件容器，容器将通过 Windows 组件模型确定位置，并将不具有访问任何 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 服务。 您可以调用 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 来获取在控件容器中的 VSPackage 服务提供程序。  
  
## 请参阅  
 [可用服务列表](../extensibility/internals/list-of-available-services.md)   
 [使用并提供服务](../extensibility/using-and-providing-services.md)   
 [服务基础知识](../extensibility/internals/service-essentials.md)