---
title: "端口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 926f5e9a80a91da57d843c11175865f78775e38c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ports"></a>端口
在调试器体系结构，方面**端口**:  
  
-   在服务器上运行一组进程的容器。 例如，端口可能表示连接到基于 Windows CE 的设备的串行电缆，或到网络的非 DCOM 机。 一个特殊的端口，称为本地端口，包含在本地计算机上运行的所有进程。  
  
-   可以将自己标识按名称或标识符。  
  
-   可枚举的端口上运行的所有进程且启动和终止这些进程。  
  
-   由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)接口，通过将传递创建[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)参数[添加](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供处理所有基于 Windows 的进程，本机和托管的默认端口。 与不基于 Windows 的外部设备，必须为连接实现一个自定义端口。 若要提供此类自定义端口，自定义端口供应商还需要实现。  
  
## <a name="see-also"></a>另请参阅  
 [服务器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [进程](../../extensibility/debugger/processes.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [添加](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)