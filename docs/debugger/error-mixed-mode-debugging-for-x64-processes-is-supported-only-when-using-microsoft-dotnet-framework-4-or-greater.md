---
title: "错误：仅当使用 Microsoft .NET Framework 4 或更高版本时才支持对 x64 进程执行混合模式调试 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.interop_unsupported_x64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误：仅当使用 Microsoft .NET Framework 4 或更高版本时才支持对 x64 进程执行混合模式调试
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要调试 64 位进程中的混合本机代码和托管代码，您必须安装了 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4 版。  低于 4 的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本不支持对 64 位进程进行混合模式调试。  
  
### 更正此错误  
  
-   执行以下步骤之一：  
  
    -   将 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 升级到 4 版。  
  
    -   生成 32 位版本的应用程序以进行调试。  
  
## 请参阅  
 [在设备上安装远程工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)