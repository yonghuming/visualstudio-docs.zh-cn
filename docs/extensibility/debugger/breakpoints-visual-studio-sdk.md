---
title: "断点 (Visual Studio SDK) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fd0eccfa45f20217291b2e00eb175f8eac49d42d
ms.lasthandoff: 02/22/2017

---
# <a name="breakpoints-visual-studio-sdk"></a>断点 (Visual Studio SDK)
有三种类型的断点︰ 挂起、 绑定和错误。  
  
 **挂起断点的一个︰**  
  
-   是包含要将断点绑定到一个或多个程序中的一个或多个代码环境所需的所有信息的抽象。 每次程序正在调试的原因代码以加载，则调试引擎将检查所有挂起断点，以查看它们是否可绑定。  
  
     挂起断点本身永远不会将绑定到代码中，但而是收集，则称包含它所生成的所有绑定的断点。  
  
-   由表示[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)接口。  
  
 **绑定的断点︰**  
  
-   是一种抽象断点与关联或绑定到单个代码上下文。 每个绑定的断点会生成挂起断点的响应。 挂起断点可以但是，生成多个绑定的断点。  
  
     卸载代码时，可以将未绑定的绑定的断点并将其丢弃。  
  
-   由表示[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)接口。  
  
 **错误断点︰**  
  
-   是用于描述错误在尝试将挂起断点绑定到代码上下文的抽象。 错误断点任一错误在位置，或者在该断点表达式本身中进行描述。 有关详细信息，请参阅[绑定断点](../../extensibility/debugger/binding-breakpoints.md)。  
  
     断点错误可以是一个错误或警告。  
  
-   由表示[IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)接口。  
  
## <a name="see-also"></a>另请参阅  
 [程序](../../extensibility/debugger/programs.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [代码上下文](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
