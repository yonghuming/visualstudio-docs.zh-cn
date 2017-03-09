---
title: "MSBuild 错误 MSB3172 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ReadInputManifestFailed"
helpviewer_keywords: 
  - "MSB3172"
ms.assetid: aa7291db-1f36-41e7-a510-90cd4daaa89d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3172
**MSB3172: 无法读取清单“\<file\>”。'  \<错误\>”**  
  
 此错误会在生成过程读取清单文件的过程中遇到错误时产生。  错误消息中包含文件名，后跟更具体的出错信息。  
  
 您可能已将程序集或清单文件作为内容文件执行了添加。  您应使用**“添加引用”**命令而不是**“添加文件”**，以便项目系统能正确引用依赖程序集。  更复杂的项目通常会将 bin 文件夹中的 .exe.manifest 标记为项目文件，您应避免此操作。  隐藏的 app.manifest 文件变为 .exe.manifest 文件，您可将它手动编辑后用于高级方案。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)