---
title: "MSBuild 错误 MSB3120 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionTooLong"
helpviewer_keywords: 
  - "MSB3120"
ms.assetid: 20bc64f5-aadc-4eec-9915-a87a3d7f81ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3120
**MSB3120: 文件关联扩展名“\<扩展名\>”超过最大允许长度 \<最大长度\>。**  
  
 文件关联扩展名中的字符数不得超过指定的数目。  
  
### 更正此错误  
  
-   将 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md) `extension` 特性设置为这样一个值：所包含的字符数不超过目标操作系统所允许的限制。  
  
## 请参阅  
 [“项目设计器”\-\>“发布”页](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)