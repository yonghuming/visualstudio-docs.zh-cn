---
title: "MSBuild 错误 MSB3123 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsCountExceedsMaximum"
helpviewer_keywords: 
  - "MSB3123"
ms.assetid: 343aa8a8-9ab9-4dd5-be59-8eccf1f3c012
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3123
**MSB3123: 文件关联数超过限制 \<限制\>。**  
  
 每个文件只允许有固定数目的关联文件扩展名。  当您尝试关联的文件扩展名数超过目标操作系统所允许的数目时，会发生此错误。  
  
### 更正此错误  
  
-   将文件关联数限制为指定数目。  
  
## 请参阅  
 [“项目设计器”\-\>“发布”页](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)