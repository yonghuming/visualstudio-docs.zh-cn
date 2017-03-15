---
title: "MSBuild 错误 MSB3185 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.NoEntryPoint"
helpviewer_keywords: 
  - "MSB3185"
ms.assetid: 032c63c5-d662-42ba-84e1-e3ccca8cee05
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3185
**MSB3185：未指定清单的入口点。**  
  
 当清单未指定入口点时，将产生此错误。  此错误既可以应用于应用程序清单，也可以应用于部署清单。  
  
### 更正此错误  
  
-   如果使用 GenerateApplicationManifest 任务，请确保指定有效的入口点，或者将 TargetFrameworkVersion 属性设置为“v3.5”或更高。  对于应用程序清单，有效的入口点是一个 .exe 文件。  
  
-   如果使用 GenerateDeploymentManifest 任务，请确保在清单中指定有效的入口点。  对于部署清单，有效的入口点是一个应用程序清单。  
  
## 请参阅  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [“项目设计器”\-\>“发布”页](../ide/reference/publish-page-project-designer.md)   
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)   
 [MSBuild 错误 MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild 错误 MSB3117](/visual-cpp/misc/msbuild-error-msb3117)   
 [MSBuild 错误 MSB3118](../misc/msbuild-error-msb3118.md)   
 [MSBuild 错误 MSB3174](/visual-cpp/misc/msbuild-error-msb3174)