---
title: "MSBuild 错误 MSB3156 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductValidation"
helpviewer_keywords: 
  - "MSB3156"
ms.assetid: 98b1bd42-9efe-44a2-8a43-476edc03590d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3156
**MSB3156: 位于“\<folder\>”的项“\<package\>”未通过 Xml 验证。**  
  
 此警告在清单（具体为 product.xml）未通过 XML 验证时产生。  具体问题在后续错误消息（[MSBuild 错误 MSB3159](/visual-cpp/misc/msbuild-error-msb3159) 或 [MSBuild 错误 MSB3160](../misc/msbuild-error-msb3160.md)）中列出。  
  
### 更正此错误  
  
-   解决后续错误消息中列出的清单验证问题。  
  
## 请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)