---
title: "事件说明 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ce3e623a2d1787aa67f8a6e4dcfcf9530e8766c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="event-descriptions"></a>事件说明
每种类型的事件有特定用途。  
  
## <a name="events-and-the-reasons-for-their-use"></a>事件和其使用的原因  
  
|Event|描述|  
|-----------|-----------------|  
|激活文档事件|发生时的调试引擎 (DE) 想 IDE 以打开或将文档置于前台。|  
|断点绑定或断点错误事件|绑定断点或当断点无法绑定，并返回一个错误时发送。|  
|未绑定的断点事件|从代码解除绑定的断点的绑定时发生。|  
|可以停止事件|发送到 IDE 以确定用户想要在代码中的指定点处停止。|  
|断点事件|代码或数据断点命中时发生。|  
|文档文本事件|在文档中的文本更改时发生。 这些事件不会通过发送`IDebugEventCallBack2::Event`方法。|  
|引擎创建事件|发送一个引擎首次创建时。|  
|入口点事件|正在调试的程序已运行其初始化代码和达到其第一个的用户入口点时发送。|  
|异常事件|发送时遇到异常时运行的程序。|  
|表达式计算完成事件|异步表达式求值完成后发送。|  
|查找符号事件|发送每当 DE 需要让用户查找的模块的符号。|  
|加载完成事件|仅当初始程序加载已完成，而且在程序中运行的第一个代码时发送。|  
|消息事件|当消息发送到用户时发送。|  
|模块加载事件|加载或卸载新的模块时发送。|  
|输出字符串事件|当程序写入调试输出时发送。|  
|创建和销毁事件|发送以宣布的创建或销毁的进程、 程序、 属性、 会话和线程，以便 Visual Studio IDE 可以跟踪的正在调试的程序的状态。|  
|步骤完成事件|步骤已完成时发送。|  
|线程名称更改事件|发送时用户更改线程的名称。|  
|程序名称更改事件|发送时用户更改程序的名称。|  
  
## <a name="see-also"></a>另请参阅  
 [发送事件](../../extensibility/debugger/sending-events.md)