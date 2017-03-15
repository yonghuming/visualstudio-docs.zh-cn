---
title: "MSBuild 错误 MSB3165 | Microsoft Docs"
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
  - "vsdeploy.chm:13165"
  - "MSBuild.GenerateBootstrapper.DifferingPublicKeys"
helpviewer_keywords: 
  - "MSB3165"
ms.assetid: 2f50462e-947d-4211-b197-e58eddcfd373
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3165
**MSB3165：“\<程序包\>”中特性“\<公钥\>”的值与文件“\<文件\>”的值不匹配。**  
  
 当引导程序包文件中指定的公匙与磁盘上可再发行包的签名不匹配，或者当可再发行包未经签名时，将出现此警告。  如果可再发行包已经过签名，则生成将采用磁盘上的包的公匙值；如果可再发行包未经签名，则采用磁盘上的包的哈希。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)   
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)