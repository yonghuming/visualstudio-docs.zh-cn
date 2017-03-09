---
title: "MSBuild 错误 MSB3186 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.NoIdentity"
helpviewer_keywords: 
  - "MSB3186"
ms.assetid: 1219fef4-9114-401c-875b-1dc69697fd9f
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3186
**MSB3186：无法从任务输入参数推导出生成的清单的程序集标识。**  
  
 当生成过程无法推断应用程序清单或部署清单的程序集名称时，就会发生此错误。  没有显式给出程序集名称；基础清单中没有标识，也未指定入口点标识。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)