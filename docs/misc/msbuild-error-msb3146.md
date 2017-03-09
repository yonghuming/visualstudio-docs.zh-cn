---
title: "MSBuild 错误 MSB3146 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
helpviewer_keywords: 
  - "MSB3146"
ms.assetid: 717fd649-3024-427d-a068-cff8034ffc0a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3146
**MSB3146: “\<package\>”需要项“\<package\>”，但未包括它。**  
  
 此错误会在以下情况下发生：一个引导程序包依赖于另一个引导程序包，但您只选择安装了前者。  例如，程序包 B 依赖于程序包 A，但仅安装了 B。  
  
### 更正此错误  
  
-   安装时要包含所需的程序包。