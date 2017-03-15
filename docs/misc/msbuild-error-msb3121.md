---
title: "MSBuild 错误 MSB3121 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationMissingAttribute"
helpviewer_keywords: 
  - "MSB3121"
ms.assetid: c1e83a2a-515f-412d-b8b7-4821e510a923
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3121
**MSB3121: 应用程序清单中的文件关联元素缺少一个或多个以下必需特性: 扩展名、说明、progid 或默认图标。**  
  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)必须包含全部四个特性的值。  
  
### 更正此错误  
  
-   将每个 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)特性设置为一个有效值。  
  
## 请参阅  
 [“项目设计器”\-\>“发布”页](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)