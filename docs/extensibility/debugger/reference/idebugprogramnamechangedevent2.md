---
title: "IDebugProgramNameChangedEvent2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
caps.latest.revision: 6
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
ms.openlocfilehash: d0032971225d25b054cd66ee500800de4bcd7b97
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
从发送调试引擎 (DE) 到会话调试管理器 (SDM) 程序的名称更改时。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugProgramNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 DE 实现此接口来报告程序的名称已更改。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)接口必须实现该接口对同一个对象。 使用 SDM [QueryInterface](/visual-cpp/atl/queryinterface)访问**IDebugEvent2**接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 DE 创建并发送此事件对象来报告程序的名称更改。 DE 发送该事件通过使用[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)时将其附加到正在调试的程序 SDM 由提供的回调函数。 自定义端口供应商发送此事件，使用我接口。  
  
## <a name="requirements"></a>要求  
 标头︰ Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll
