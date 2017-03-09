---
title: "MSBuild 错误 MSB3143 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CopyPackageError"
helpviewer_keywords: 
  - "MSB3143"
ms.assetid: b4278c8c-31df-4b4f-9ef9-7b9327e8ee77
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3143
**MSB3143: 尝试复制“\<package\>”项的“\<file\>”时出错: \<error\>**  
  
 此错误会在引导程序包被复制到生成输出目录时发生。  导致此错误的可能原因是：  
  
-   您没有向生成输出目录复制内容的权限。  
  
-   磁盘已满。  
  
 这些也是 file.copy 或 directory.createdirectory 失败的潜在原因。  
  
## 请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)