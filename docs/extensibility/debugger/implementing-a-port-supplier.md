---
title: "实现的端口供应商提供 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3bc985bf9fb55b67b5a332f007abe98c6718fbf2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-a-port-supplier"></a>实现端口供应商
端口供应商提供对会话调试管理器 (SDM) 请求的端口。 端口供应商需要调试到非 DCOM 机时或当新设备需要支持时实现。 例如，若要提供了与移动电话的调试，则可能会实现提供端口连接到移动电话 （可能通过 IR 或单元格连接） 和枚举的进程和手机上运行的程序的端口供应商提供。  
  
 对于基于 Windows 的计算机 （包括远程调试） 上的调试程序，Visual Studio 提供端口供应商的本机和公共语言运行时 (CLR) 进程，因此无需在这些情况下实现你自己的端口提供程序。  
  
## <a name="in-this-section"></a>本节内容  
 [实现和注册端口提供程序](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 讨论如何 SDM 交互端口提供程序和其端口通信。  
  
 [所需的端口提供程序接口](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 文档必须实现以获取的端口供应商提供的接口。  
  
## <a name="related-sections"></a>相关章节  
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)  
 描述调试的主要体系结构概念。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 调试器可扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)