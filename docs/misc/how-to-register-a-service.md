---
title: "如何：注册服务 | Microsoft Docs"
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
  - "服务, 注册"
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# 如何：注册服务
托管包框架 \(MPF\) 提供一些特性来控制托管服务的注册。 RegPkg 实用工具使用这些特性向 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 注册服务。  
  
## 示例  
 下面的代码来自 [VSSDK 示例](../misc/vssdk-samples.md)。  
  
 [!code-vb[VSSDKRegisterService#1](../misc/codesnippet/VisualBasic/how-to-register-a-service_1.vb)]
 [!code-cs[VSSDKRegisterService#1](../misc/codesnippet/CSharp/how-to-register-a-service_1.cs)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 向 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 注册 SMyGlobalService 服务。 有关 <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> 和 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 的更多信息，请参见[注册和注销 VSPackages 迁移](../extensibility/registering-and-unregistering-vspackages.md)。  
  
 若要注册一个服务来替换另一个同名服务，请使用 <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>，而不是 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>。  
  
## 可靠编程  
 为了便于重新编译服务提供程序而不更改服务客户端（反之亦然），可以在单独的程序集模块中定义服务及其接口。 下面的代码来自 Reference.Services \(C\#\) 示例中的 IMyGlobalService.cs 文件。  
  
 [!code-vb[VSSDKRegisterService#2](../misc/codesnippet/VisualBasic/how-to-register-a-service_2.vb)]
 [!code-cs[VSSDKRegisterService#2](../misc/codesnippet/CSharp/how-to-register-a-service_2.cs)]  
  
 若要从非托管代码获取接口，需使用 <xref:System.Runtime.InteropServices.ComVisibleAttribute>。  
  
> [!NOTE]
>  虽然可以对服务和接口使用相同的类型或 GUID，但建议将两者分开，因为一个服务可能会公开多个不同的接口。  
  
## 请参阅  
 [Registering VSPackages](http://msdn.microsoft.com/zh-cn/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [服务基础知识](../extensibility/internals/service-essentials.md)