---
title: "MSBuild 错误 MSB3175 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidItemValue"
helpviewer_keywords: 
  - "MSB3175"
ms.assetid: c157e934-e4e6-43d9-abdf-cb4fb03be494
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3175
**MSB3175: 项“\<build task\>”的“\<file\>”的值无效。**  
  
 此警告会在以下情况下产生：生成过程未识别各种基于枚举的任务项属性的值，如 `AssemblyType`、`DependencyType`、`FileType` 或 `TargetZone`。  适用于应用程序清单和部署清单。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)