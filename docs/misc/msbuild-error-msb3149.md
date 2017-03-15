---
title: "MSBuild 错误 MSB3149 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoResources"
helpviewer_keywords: 
  - "MSB3149"
ms.assetid: 63857405-d420-457d-9ba7-80e1a2a9dcb7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3149
**MSB3149：没有可用于生成引导程序的资源。**  
  
 当未能找到与任何区域性相匹配的引导程序资源文件 \(setup.xml\) 时，将发生此错误。  
  
### 更正此错误  
  
-   转到**“控制面板”**，选择**“添加或删除程序”**，修复 Visual Studio SDK 或将这些文件复制到适当的目录（\<SDK 安装路径\>\\bootstrapper\\engine\\\<区域性\>\\setup.xml）。  
  
## 请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)