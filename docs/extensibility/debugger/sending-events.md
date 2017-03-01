---
title: "在将事件发送 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 7
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
ms.openlocfilehash: edd4abfa31b309290bdb07fd98c104a279d98fc7
ms.lasthandoff: 02/22/2017

---
# <a name="sending-events"></a>发送事件
调试器和调试引擎 (DE) 之间的通信的机制是基于 DCOM 的事件模型。 将事件发送为 COM 对象，并每个事件具有参数，指定下列各项︰  
  
-   调用该事件 DE。  
  
-   说明发生了什么情况。  
  
-   进程、 程序和线程标识的事件发生在上下文的信息。 该过程不会发送从 DE 发送的事件。  
  
-   用于指示事件是同步还是异步的事件类型。  
  
 使用该方法发送所有调试事件[IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [事件源](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 解释事件的两个源︰ 调试引擎 (DE) 和会话调试管理器 (SDM)。  
  
 [支持的事件类型](../../extensibility/debugger/supported-event-types.md)  
 讨论的当前支持的事件类型︰ 异步和同步。  
  
 [事件描述](../../extensibility/debugger/event-descriptions.md)  
 定义事件和为其使用的原因。  
  
## <a name="related-sections"></a>相关章节  
 [创建自定义调试引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 介绍 DE 使用解释程序或操作系统提供调试服务的工作方式。
