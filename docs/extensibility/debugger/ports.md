---
title: "端口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "端口"
  - "调试 [调试 SDK]，端口"
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 端口
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

根据调试器体系结构， **端口**:  
  
-   是的容器将进程运行在服务器。  例如，端口可能是由另一个序列化的电缆表示连接与基于 windows CE 的计算机，或与一个以上网络非 DCOM 计算机。  特定端口，调用本地端口，包含所有进程运行在本地计算机上。  
  
-   可以按名称标识其自身或标识符。  
  
-   可以枚举上运行的所有进程端口和启动和停止这些过程。  
  
-   由 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 接口表示，通过将 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 参数创建对 [添加端口](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供处理基于 windows 的所有进程中的默认端口，本机和管理。  必须只适用于基于 windows 的外部计算机的连接实现自定义端口。  还提供此类自定义端口，自定义端口提供程序需要实现。  
  
## 请参阅  
 [服务器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [进程](../../extensibility/debugger/processes.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [添加端口](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)