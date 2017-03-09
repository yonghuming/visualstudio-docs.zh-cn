---
title: "MSBuild 错误 MSB3486 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertificateError"
helpviewer_keywords: 
  - "MSB3486"
ms.assetid: 75d03d8e-3a28-4010-b602-61fe037dec74
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3486
**MSB3486：无法从存储区“\<certificate store\>”获取证书。**  
  
 当未在个人证书存储区中找到与项目的 .pfx 文件的指纹匹配的证书时，`ResolveKeySource` MSBuild 任务将产生此错误。  
  
### 更正此错误  
  
-   确保项目的 .pfx 文件的指纹与个人证书存储区中的证书的指纹相匹配。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)