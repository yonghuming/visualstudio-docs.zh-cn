---
title: "如何：使用 GetGlobalService | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "服务, GetGlobalService"
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# 如何：使用 GetGlobalService
有时可能需要获取从非网站的工具窗口或控件容器中服务，或者已经放置与不知道服务所需的服务提供程序。  例如，您可能希望同时写入事件日志从控件内部。  有关这些属性和其他方案的更多信息，请参见 [如何: 解决服务疑难问题](../extensibility/how-to-troubleshoot-services.md)。  
  
 通过调用静态 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 方法来获得大多数 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 服务。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 依赖于第一次初始化 <xref:Microsoft.VisualStudio.Shell.Package> 从派生的所有 VSPackage 站点的已缓存的服务提供程序。  您必须确保此条件匹配，或者为空服务准备。  
  
 幸运的是， <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 大多数时候正常工作。  
  
-   如果 VSPackage 对于其他 VSPackage 仅提供已知的某项服务，请求的 VSPackage 服务网站，在提供服务的 VSPackage 加载之前。  
  
-   如果工具窗口是由 VSPackage 创建， VSPackage 站点，在工具窗口之前。  
  
-   如果控件容器受到 VSPackage 创建的工具窗口承载， VSPackage 站点，在控件容器之前。  
  
### 获取工具窗口或控件容器的内部一个服务  
  
-   插入此代码在构造函数、工具窗口或控件容器:  
  
     [!code-vb[UseGetGlobalService#1](../misc/codesnippet/VisualBasic/how-to-use-getglobalservice_1.vb)]
     [!code-cs[UseGetGlobalService#1](../misc/codesnippet/CSharp/how-to-use-getglobalservice_1.cs)]  
  
     此代码获取一 SVsActivityLog 服务并将其强制 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 接口，可用于向事件日志中写入。  有关示例，请参见[如何︰ 使用活动日志](../extensibility/how-to-use-the-activity-log.md)。  
  
## 请参阅  
 [如何: 解决服务疑难问题](../extensibility/how-to-troubleshoot-services.md)   
 [使用并提供服务](../extensibility/using-and-providing-services.md)   
 [服务基础知识](../extensibility/internals/service-essentials.md)