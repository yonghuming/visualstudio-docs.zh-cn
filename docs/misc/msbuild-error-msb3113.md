---
title: "MSBuild 错误 MSB3113 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ResolveFailedInReadWriteMode"
helpviewer_keywords: 
  - "MSB3113"
ms.assetid: 81e73738-e6ee-4651-9f48-acb1feef3ff5
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3113
**MSB3113: 未能找到文件“\<文件\>”。**  
  
 在创建新清单的过程中，如果遇到无法解析的引用，就会产生此错误。  此错误可能源自项目文件，也可能由任务参数造成。  
  
### 更正此错误  
  
-   检查您的项目文件是否存在文件引用冲突，如果正在进行自定义生成，还要检查生成参数。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)