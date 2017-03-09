---
title: "MSBuild 错误 MSB3119 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionMissingLeadDot"
helpviewer_keywords: 
  - "MSB3119"
ms.assetid: 52d68b0e-01d4-436f-a96c-733fd20a8c04
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3119
**MSB3119: 文件关联扩展名必须以句点字符\(.\)开头。**  
  
 如果配置文件关联时文件关联扩展名不是以句点字符 \(.\) 开头的，将发生此错误。  
  
### 更正此错误  
  
-   将 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md) `extension` 特性设置为以句点字符 \(.\) 开头的值，例如，“.doc”。  
  
## 请参阅  
 [“项目设计器”\-\>“发布”页](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)