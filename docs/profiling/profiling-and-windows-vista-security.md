---
title: "分析和 Windows Vista 安全性 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ac59d9cb4b729b99193a921c5f6965e48815261
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="profiling-and-windows-vista-security"></a>分析和 Windows Vista 安全性
根据计算机管理员提供的 [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] 用户访问权限设置，单个用户可能会具有在该计算机上分析进程的安全权限。 下面的示例说明了用户之间可能存在的差异：  
  
-   当管理员启动了驱动程序和服务时，某些用户可能会访问高级分析功能。  
  
-   域用户仅可访问样本分析。  
  
-   某些用户可能拒绝分析其他所有用户的访问权限。  
  
 有关详细信息，请参阅 [VSPerfCmd](../profiling/vsperfcmd.md) 中的“管理员”选项。  
  
## <a name="cross-session-profiling"></a>跨会话分析  
 *跨会话分析*是分析在不同登录会话中运行的进程的能力。 例如，大多数服务在会话 0 中运行，而用户无法直接在会话 0 中运行。 使用性能资源管理器工具栏上的“附加到进程”按钮或 VSPerfCmd 命令行工具的 /attach 选项可以分析不同登录会话中的大多数进程。  
  
 可以通过设置跨进程分析可见性选项来查看可用进程的列表。 在单击“附加到进程”时显示的“附加到进程”窗口中提供了这些选项：  
  
-   **显示所有用户的进程**  
  
     未选择此选项时，列表只显示当前用户所拥有的进程。 选择“显示所有用户的进程”时，列表显示所有用户的进程。  
  
-   **显示所有会话中的进程**  
  
     未选择此选项时，列表显示当前会话中的进程。 选择此选项时，列表显示所有会话中的进程。  
  
## <a name="see-also"></a>另请参阅  
 [概述](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [如何：附加到运行的进程](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)