---
title: "MSBuild 错误 MSB3188 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.PrerequisiteNotSigned"
helpviewer_keywords: 
  - "MSB3188"
ms.assetid: 8520e960-3b31-4e25-9fce-b9092b869bd0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3188
**MSB3188: 要将程序集“\<assembly\>”标记为系统必备，必须对其进行强签名。**  
  
 此错误会在必备程序集未进行强签名时产生。  它仅适用于应用程序清单。  
  
### 更正此错误  
  
-   确保项目所使用的所有程序集均经过强签名。