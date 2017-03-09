---
title: "MSBuild 错误 MSB3145 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidUrl"
helpviewer_keywords: 
  - "MSB3145"
ms.assetid: 183d4e7e-bdc6-402f-a1b6-531505be605f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3145
**MSB3145: 生成输入参数“\<属性\>\=\<值\>”不是 Web URL 或 UNC 共享。**  
  
 当 `SupportUrl`、`ComponentsUrl` 或 `ApplicationUrl` 项目属性的值无效时，便会发生此错误。  该值必须是有效的 URI 或 UNC 路径。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)