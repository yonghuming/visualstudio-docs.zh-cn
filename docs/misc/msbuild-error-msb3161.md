---
title: "MSBuild 错误 MSB3161 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CircularDependency"
helpviewer_keywords: 
  - "MSB3161"
ms.assetid: 2871d071-7c3a-4103-8b14-6ee56564a7f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3161
**MSB3161：在以下生成包中检测到一个循环依赖项: “\<package\>”。**  
  
 当引导程序包依赖项关系图中存在循环依赖项（例如，A→B→C→A）时，就会产生此警告。  在这种情况下，引导程序无法确定要先安装哪个包。  
  
### 更正此错误  
  
-   通过更改引导程序包文件中描述的依赖项，或不安装相互依赖的包之一，从而移除循环依赖项。  
  
## 请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)