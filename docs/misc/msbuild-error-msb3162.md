---
title: "MSBuild 错误 MSB3162 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.DependencyNotFound"
helpviewer_keywords: 
  - "MSB3162"
ms.assetid: 35189e5d-c065-4d57-bf78-6433771a5063
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3162
**MSB3162: 项“\<package\>”未能找到依赖项“\<package\>”。**  
  
 此错误会在以下情况下发生：一个引导程序包依赖于另一个引导程序包，但无法找到前者的系统必备的清单。