---
title: "MSBuild 错误 MSB3144 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.InvalidInput"
helpviewer_keywords: 
  - "MSB3144"
ms.assetid: 955e0db3-afe2-4c03-8e95-3419878374df
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3144
**MSB3144：未提供足够的数据来生成引导程序。  请至少提供参数“ApplicationFile”或“BootstrapperItems”之一的值。**  
  
 当没有提供足够的数据以生成引导程序时，就会发生此错误。  生成过程将创建一个没有应用安装程序和包的空引导程序。  
  
### 更正此错误  
  
-   至少提供参数 `ApplicationFile` 或 `BootstrapperItems` 之一的值。  
  
## 请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)