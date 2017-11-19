---
title: "IDebugThreadCall 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b2b1b500aec08520166d9092edfa6a58c1df0fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall 接口
`IDebugThreadCall`接口通常由与跨线程调用的组件实现`IDebugThread`封送处理过程调试管理器 (PDM) 提供的实现。  
  
 PDM 调用`IDebugThreadCall`中所需的线程，接口和`IDebugThreadCall`接口将调度到的所需的实现调用。 `IDebugThreadCall`接口将强制转换到相应的页首参数中传递的参数信息。  
  
 `IDebugThreadCall`接口是自由线程对象。  
  
## <a name="methods"></a>方法  
 除了从继承的方法`IUnknown`、`IDebugThreadCall`接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|处理调用另一线程中运行代码。|