---
title: "指定分析工具命令行工具的路径 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 指定分析工具命令行工具的路径
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令行工具的路径不添加到 PATH 环境变量中。  在 32 位计算机上，这些工具位于单个目录中。  64 位计算机上有这些分析工具的 32 位和 64 位版本。  
  
## 32 位计算机  
 在 32 位计算机上，默认的探查器工具目录为 *Drive*\\Program Files\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools。  
  
## 64 位计算机  
 在 64 位计算机上，根据被分析应用程序的目标平台指定路径。  
  
-   对于 32 位应用程序，默认的探查器工具目录为：  
  
     *Drive*\\Program Files \(x86\)\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools  
  
-   对于 64 位应用程序，默认的探查器工具目录为：  
  
     *Drive*\\Program Files \(x86\)\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools\\x64