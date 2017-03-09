---
title: "MSBuild 错误 MSB3166 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageResourceFileNotFound"
  - "vsdeploy.chm:13166"
helpviewer_keywords: 
  - "MSB3166"
ms.assetid: f5dff83a-1e41-4c92-a137-89b7e9f3cd93
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3166
**MSB3166: 未能找到项“\<程序包\>”所需的文件“\<文件\>”。**  
  
 缺少最终用户许可协议 \(EULA\) 或外部检查文件时会产生此错误。  确保磁盘上存在该文件。  
  
### 更正此错误  
  
-   重新安装 Visual Studio SDK  
  
     \- 或 \-  
  
-   将所需的文件复制到相应的位置。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)