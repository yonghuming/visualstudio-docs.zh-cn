---
title: "MSBuild 错误 MSB3118 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.UseApplicationTrustInvalidFrameworkVersion"
helpviewer_keywords: 
  - "MSB3118"
ms.assetid: 9bf5b430-0cfb-4da5-a7f7-04d69f20cce1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3118
**MSB3118: 应用程序设置为使用应用程序信任，但 TargetFrameworkVersion 不是 v3.5。**  
  
 在将 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A> 属性设置为 `True` 并将 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> 属性设置为低于 `v3.5` 的版本（例如，`v2.0`）时，便会发生此错误。  
  
### 更正此错误  
  
-   将 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> 属性设置为 `v3.5` 或更高版本。  
  
## 请参阅  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 [“项目设计器”\-\>“发布”页](../ide/reference/publish-page-project-designer.md)   
 [MSBuild 错误 MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild 错误 MSB3117](/visual-cpp/misc/msbuild-error-msb3117)   
 [MSBuild 错误 MSB3119](../misc/msbuild-error-msb3119.md)   
 [MSBuild 错误 MSB3174](/visual-cpp/misc/msbuild-error-msb3174)   
 [MSBuild 错误 MSB3185](../misc/msbuild-error-msb3185.md)