---
title: "MSBuild 错误 MSB3481 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertNotInStore"
helpviewer_keywords: 
  - "MSB3481"
ms.assetid: 55f99775-3bd5-4e1b-b184-c6405d75e8ff
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3481
**MSB3481：未能找到签名证书。  请确保它在当前用户的个人存储区中。**  
  
 当未在个人证书存储区中找到签名证书时，将产生此错误。  此错误类似于 [MSBuild 错误 MSB3486](../misc/msbuild-error-msb3486.md)（表示找到了证书，但证书不匹配）。  
  
### 更正此错误  
  
-   确保与项目的 .pfx 文件相匹配的有效证书在个人证书存储区中。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)