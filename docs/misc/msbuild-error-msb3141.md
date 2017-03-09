---
title: "MSBuild 错误 MSB3141 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.MissingVerificationInformation"
  - "vsdeploy.chm:13141"
helpviewer_keywords: 
  - "MSB3141"
ms.assetid: f32ce5fd-bb82-4a8b-aebe-61efef89cdc1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3141
**MSB3141：没有为项“\<包\>”的文件“\<文件\>”指定“PublicKey”或“Hash”特性。**  
  
 当尝试将 HomeSite 用于引导程序包时，将发生此错误。  但是，引导程序清单不包含用于运行时文件验证的正确信息（公钥或哈希）。  
  
### 更正此错误  
  
-   下载缺少信息的包，并将该包复制到引导程序缓存中。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)