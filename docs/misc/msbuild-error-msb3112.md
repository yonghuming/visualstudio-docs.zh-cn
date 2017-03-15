---
title: "MSBuild 错误 MSB3112 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateAssemblyIdentity"
helpviewer_keywords: 
  - "MSB3112"
ms.assetid: 90f25254-8148-49ea-9a5a-213feda16df0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3112
**MSB3112: 两个或多个程序集具有相同的标识“\<程序集\>”。**  
  
 当多个被引用的程序集具有相同的标识时，便会产生此警告。  
  
### 更正此错误  
  
-   从项目中移除被引用的程序集中的一个。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)