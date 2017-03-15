---
title: "MSBuild 错误 MSB3176 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.GreaterMinimumRequiredVersion"
helpviewer_keywords: 
  - "MSB3176"
ms.assetid: 9138f5ce-4af6-428e-8ac4-c4390a154daf
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3176
**MSB3176：指定最低要求的版本高于当前的发布版本。  请指定一个低于或等于当前发布版本的版本。**  
  
 当要求的最低应用程序版本大于部署清单的当前版本时，将产生此错误。  
  
### 更正此错误  
  
-   指定一个低于或等于当前发布版本的最低要求版本。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)