---
title: "如何：指定 .NET Framework 运行时 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 894d3f137787617de88ddcd2bed586c64dd22117
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-specify-the-net-framework-runtime"></a>如何：指定 .NET Framework 运行时
[!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] 发布后，应用程序可以由使用不同的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 运行时版本生成的模块构成。 默认情况下，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具会分析应用程序加载的第一个运行时。 用探查器启动应用程序时，以及将探查器附加到已在运行的应用程序时，可以指定要分析的运行时。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>用探查器启动应用程序时指定要分析的 .NET Framework 运行时  
  
1.  在“性能资源管理器”中，右键单击性能会话，单击“属性”，然后单击“高级”。  
  
     “目标 CLR 版本”列表框将显示“自动”以及计算机上安装的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 运行时版本。  
  
2.  执行以下步骤之一：  
  
    -   单击要分析的 CLR 版本。  
  
    -   单击“自动”分析应用程序加载的第一个版本。  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>将探查器附加到应用程序时指定要分析的 .NET Framework 运行时  
  
1.  在“分析”菜单上，指向“探查器”，然后单击“附加/分离”。  
  
2.  在“将探查器附加到进程”对话框中，单击要分析的进程。  
  
     “目标 CLR 版本”列表框将显示“自动”以及计算机上安装的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 运行时版本。  
  
3.  执行以下步骤之一：  
  
    -   单击要分析的 CLR 版本。  
  
    -   单击“自动”分析探查器附加到应用程序时加载的版本。