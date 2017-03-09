---
title: "MSBuild 错误 MSB3150 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.NoStringsForCulture"
helpviewer_keywords: 
  - "MSB3150"
ms.assetid: 90d86aef-f4df-4070-8ecc-173eb40668aa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3150
**MSB3150: 没有可用于生成引导程序区域性为“{0}”的字符串资源。**  
  
 当 setup.xml 已找到但其中未包含字符串节点时，便会发生此错误。  XML 文件可能已损坏。  
  
### 更正此错误  
  
-   转到**“控制面板”**，选择**“添加或删除程序”**，修复 Visual Studio SDK 或将这些文件复制到适当的目录（\<SDK 安装路径\>\\bootstrapper\\engine\\\<区域性\>\\setup.xml）。