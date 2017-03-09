---
title: "如何：从 DTE 对象获取服务 | Microsoft Docs"
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
  - "服务，从 DTE 对象。"
ms.assetid: c26a51d4-86f0-454b-9625-5443e55eec7d
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# 如何：从 DTE 对象获取服务
服务可以从访问 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 自动 <xref:EnvDTE.DTEClass> 对象的所有过程中获取的。  例如，通过 DTE 对象访问从向导的 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 服务。  可以使用此服务到写入事件日志。  有关更多信息，请参见 [如何︰ 使用活动日志](../extensibility/how-to-use-the-activity-log.md)。  
  
 DTE 对象实现 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>，使用 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>，可用于从托管代码中的服务查询。  
  
### 获取从 DTE 对象的一个服务  
  
1.  下面的代码创建从 DTE 对象的 <xref:Microsoft.VisualStudio.Shell.ServiceProvider> 并调用与 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 服务类型的 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 。  服务被强制转换为接口 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>，用于编写项操作日志。  有关更多信息 abou 对事件日志的编写方式，请参见 [如何︰ 使用活动日志](../extensibility/how-to-use-the-activity-log.md)。  
  
     [!code-cs[GetAServiceFromTheDTEObject#1](../misc/codesnippet/CSharp/how-to-get-a-service-from-the-dte-object_1.cs)]
     [!code-vb[GetAServiceFromTheDTEObject#1](../misc/codesnippet/VisualBasic/how-to-get-a-service-from-the-dte-object_1.vb)]  
  
## 请参阅  
 [使用并提供服务](../extensibility/using-and-providing-services.md)   
 [服务基础知识](../extensibility/internals/service-essentials.md)