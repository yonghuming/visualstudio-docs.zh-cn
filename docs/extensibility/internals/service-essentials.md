---
title: "服务 Essentials |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 006ab3b57a21d5b9a661f06bc984f4dca8757bfd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="service-essentials"></a>服务 Essentials
服务是两个 Vspackage 之间的协定。 一个 VSPackage 提供一组特定的接口，另一个 VSPackage 来使用。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本身就是向其他 Vspackage 提供服务的 Vspackage 集合的形式。  
  
 例如，SVsActivityLog 服务可用于获取 IVsActivityLog 接口，它可用于写入活动日志。 有关详细信息，请参阅[如何： 使用活动日志](../../extensibility/how-to-use-the-activity-log.md)。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]此外提供了一些内置服务未注册。 Vspackage 可以通过提供服务重写替换内置或其他服务。 仅一个服务重写被允许的任何服务。  
  
 服务具有任何可发现性。 因此，你必须知道你想要使用，服务的服务标识符 (SID)，而且你必须知道它提供的接口。 该服务的参考文档提供此信息。  
  
-   提供服务的 Vspackage 称为服务提供商。  
  
-   向其他 Vspackage 提供的服务称为全球服务。  
  
-   仅适用于 VSPackage 实现它们，或到它创建的任何对象，称为本地服务的服务。  
  
-   替换内置的服务或所提供的其他包中，服务的服务称为服务重写。  
  
-   按需加载服务或服务重写，后，它提供的服务请求由另一个 VSPackage 时，即加载服务提供程序。  
  
-   若要支持按需加载，服务提供程序注册其全球服务和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 有关详细信息，请参阅[如何： 提供服务](../../extensibility/how-to-provide-a-service.md)。  
  
-   获取服务后，使用[QueryInterface](/cpp/atl/queryinterface) （非托管代码） 或强制转换 （托管代码） 来获取所需的接口，例如：  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    ```  
  
-   托管的代码是指按照其类型的服务而非托管的代码是指由其 GUID 的服务。  
  
-   当[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]加载 VSPackage，它将传递服务提供商给 VSPackage 全球服务使 VSPackage 能够访问。 这称为"安置功能"VSPackage。  
  
-   Vspackage 可以是服务提供商他们创建的对象。 例如，窗体可能会将颜色服务的请求发送到其进行处理，从而可能将传递到请求[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   深度嵌套，或在所有位置不正确的托管的对象可以调用<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>直接访问全球服务。   
  
<a name="how-to-use-getglobalservice"></a>  
  
## <a name="use-getglobalservice"></a>使用 GetGlobalService  
  
有时你可能需要从工具窗口中获得的服务或控制容器不放置，或是已放置一个并不了解所需的服务的服务提供商。 例如，你可能想要写入到的活动日志从控件内。 有关这些和其他方案的详细信息，请参阅[如何： 解决服务](../../extensibility/how-to-troubleshoot-services.md)。  
  
你可以通过调用静态获取大多数 Visual Studio 服务<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法。  
  
<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>依赖于缓存服务上放置初始化首次从包派生的任何 VSPackage 的提供程序。 必须保证此条件满足时，，，否则是 null 服务为做好准备。  
  
幸运的是，<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>正常大部分时间。  
  
-   如果 VSPackage 提供了另一个 VSPackage 只有知道服务，请求该服务 VSPackage 占位之前提供此服务已加载 VSPackage。  
  
-   如果工具窗口由 VSPackage 创建的则 VSPackage 占创建工具窗口之前位。  
  
-   如果通过创建 VSPackage 的工具窗口托管的控件容器，则 VSPackage 占之前创建的控件容器位。  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>若要获得从工具窗口或控件容器中的服务  
  
-   构造函数、 工具窗口或控件容器中插入此代码：  
  
    ```csharp  
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```  
    ```vb  
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```  
    
    此代码包含 SVsActivityLog 服务，并将其强制转换为 IVsActivityLog 接口，它可以用于写入活动日志。 有关示例，请参阅[如何： 使用活动日志](../../extensibility/how-to-use-the-activity-log.md)。  
  
## <a name="see-also"></a>另请参阅  
 [可用服务列表](../../extensibility/internals/list-of-available-services.md)   
 [使用和提供服务](../../extensibility/using-and-providing-services.md)   
 [强制转换和类型转换](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [强制转换](/cpp/cpp/casting)