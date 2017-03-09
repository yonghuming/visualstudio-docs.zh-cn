---
title: "MSBuild 错误 MSB3124 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsDuplicateExtensions"
helpviewer_keywords: 
  - "MSB3124"
ms.assetid: d8365103-aa9d-400e-9c24-0a43e2bfbd14
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3124
**MSB3124: 已经为扩展名“\<扩展名\>”创建文件关联。**  
  
 遇到重复文件关联扩展名时会发生此错误。  
  
### 更正此错误  
  
-   移除不唯一的 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md) `extension` 特性。  每个列出的 \<文件关联\> 元素的扩展名特性都必须唯一。  
  
## 请参阅  
 [“项目设计器”\-\>“发布”页](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)