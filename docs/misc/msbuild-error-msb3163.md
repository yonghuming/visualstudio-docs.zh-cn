---
title: "MSBuild 错误 MSB3163 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidComponentsLocation"
helpviewer_keywords: 
  - "MSB3163"
ms.assetid: 35c5efbf-2fd7-478c-bb8e-3c4eabb3e4d4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3163
**MSB3163: 生成输入参数“ComponentsLocation\='\<ComponentsLocation\>”无效。  该值必须为“HomeSite”、“Relative”或“Absolute”之一。  默认为“HomeSite”。**  
  
 此错误在 `ComponentsLocation` 属性的指定值（表示安装必备组件的位置）无效时发生。  `ComponentsLocation` 应是下列三个值之一：`HomeSite`、`Relative` 或 `Absolute`。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)