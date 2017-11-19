---
title: "断点 (Visual Studio SDK) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8acb93b9e079dbfc3abf5083734b9b4ec392e1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="breakpoints-visual-studio-sdk"></a>断点 (Visual Studio SDK)
有三种类型的断点： 挂起绑定和错误。  
  
 **挂起断点的一个：**  
  
-   是包含将断点绑定到一个或多个程序中的一个或多个代码上下文所需的所有信息的抽象。 每次的调试引擎程序正在调试的原因代码加载的代码，检查所有挂起断点，以查看是否可以将它们绑定。  
  
     挂起断点本身永远不会将绑定到代码中，而是收集和称为包含它生成的所有绑定的断点。  
  
-   由[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)接口。  
  
 **绑定的断点：**  
  
-   是针对某个断点的抽象与关联，或绑定到单个代码上下文。 响应挂起断点以生成每个绑定的断点。 挂起断点但是，可以生成多个绑定的断点。  
  
     卸载程序代码时，则可以未绑定的绑定的断点，并将其丢弃。  
  
-   由[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)接口。  
  
 **错误断点：**  
  
-   是用于在尝试将挂起断点绑定到代码上下文描述错误的抽象。 错误断点描述任一错误位于位置或在该断点表达式本身。 有关详细信息，请参阅[绑定断点](../../extensibility/debugger/binding-breakpoints.md)。  
  
     断点错误可以是错误或警告。  
  
-   由[IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)接口。  
  
## <a name="see-also"></a>另请参阅  
 [程序](../../extensibility/debugger/programs.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [代码上下文](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)