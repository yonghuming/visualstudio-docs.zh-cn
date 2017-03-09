---
title: "MSBuild 错误 MSB3152 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
helpviewer_keywords: 
  - "MSB3152"
ms.assetid: 5a3859d4-4107-4e46-bb42-04de92b551de
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3152
**MSB3152：系统必备的安装位置未设置为“组件供应商的网站”，无法在磁盘上找到项“\<package\>”中的文件“\<file\>”。  有关更多信息，请参见帮助。**  
  
 当缺少必备安装程序所需的文件时，会发生此错误。  安装程序文件放置在 Visual Studio 为可再发行组件包保留的特殊文件夹中。  该文件夹随开发所用的 Visual Studio 版本而异。  有关该特定文件夹位置的更多信息，请参见 [创建引导程序包](../deployment/creating-bootstrapper-packages.md)。  
  
### 更正此错误  
  
-   确定该文件是否在磁盘上存在。  
  
-   使用 HomeSite 尝试解决该包问题。  
  
-   在项目文件中将 `CopyComponents` 设置为 `false`。  
  
-   不要使用损坏的引导程序包。  
  
## 请参阅  
 [创建引导程序包](../deployment/creating-bootstrapper-packages.md)