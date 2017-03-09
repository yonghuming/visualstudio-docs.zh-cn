---
title: "MSBuild 错误 MSB3128 | Microsoft Docs"
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
  - "GenerateManifest.ManifestsSignedHashExcluded"
helpviewer_keywords: 
  - "MSB3128"
ms.assetid: e8612a4b-4016-48d2-b5f0-a1091bfe8cb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3128
**MSB3128: 无法对 ClickOnce 清单进行签名，因为它们包含一个或多个未进行散列的引用。\[MSB3128: The ClickOnce manifests cannot be signed because they contain one or more references that are not hashed.\]**  
  
 发布具有已签名清单的应用程序时，所有文件都必须包含在哈希中。  
  
### 更正此错误  
  
1.  进入**“项目设计器”**的**“发布”**页。  
  
2.  单击**“应用程序文件”**。  
  
3.  对要发布的所有文件将**“哈希”**设置为**“包含”**。  
  
## 请参阅  
 [“项目设计器”\-\>“发布”页](../ide/reference/publish-page-project-designer.md)