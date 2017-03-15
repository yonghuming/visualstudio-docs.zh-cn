---
title: "MSBuild 错误 MSB3164 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageHomeSiteMissing"
helpviewer_keywords: 
  - "MSB3164"
ms.assetid: 5a1e31fc-0322-4d4e-8c26-013b1efb82c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3164
**MSB3164：没有为“\<包\>”提供“HomeSite”特性，因此包将被发布到引导程序所在的位置。**  
  
 当用户希望使用 HomeSite，但指定包的适当 HomeSite 信息不可用时，将生成此警告。  
  
### 更正此错误  
  
-   更新清单文件以包括 HomeSite 信息。  
  
-   也可以选择不使用 HomeSite。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)