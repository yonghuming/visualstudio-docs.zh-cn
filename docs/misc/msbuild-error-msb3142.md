---
title: "MSBuild 错误 MSB3142 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.CopyError"
helpviewer_keywords: 
  - "MSB3142"
ms.assetid: acca7437-6c72-446c-a6b5-a1c051b6855f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3142
**MSB3142：尝试将“\<file\>”复制到“\<folder\>”时出错: “\<error\>”**  
  
 此错误是在将 setup.bin 复制到生成输出目录时产生的。  导致此错误的可能原因是：  
  
-   您没有向输出目录复制内容的权限。  
  
-   磁盘已满。  
  
 这些也是 file.copy 或 directory.createdirectory 失败的潜在原因。  
  
## 请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)