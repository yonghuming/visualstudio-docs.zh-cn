---
title: "MSBuild 错误 MSB3151 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
helpviewer_keywords: 
  - "MSB3151"
ms.assetid: e4766734-2e90-436e-850b-a8a9da535dee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3151
**MSB3151: 项“\<package\>”已包含“\<package\>”。**  
  
 此警告会在以下情况下发生：您选择了两个引导程序包，其中一个程序包包含在另一个之中（例如，选择被包含的程序包则出现冗余）。  
  
### 更正此错误  
  
-   为冗余包含的程序包清除复选框。