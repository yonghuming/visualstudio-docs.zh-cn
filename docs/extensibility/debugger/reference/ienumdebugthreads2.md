---
title: "IEnumDebugThreads2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugThreads2
helpviewer_keywords: IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca4fedeb7e52fff627a8fab9e100c0a99792f1c6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
此 interfac 枚举在当前调试会话中运行的线程。  
  
## <a name="syntax"></a>语法  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口来表示在程序中的线程的列表。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)获取表示列表中的进程中运行的所有程序的所有线程的此接口。 调用[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)以获取此接口，表示在程序中运行的线程的列表。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IEnumDebugThreads2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一篇](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|检索指定的枚举序列中的线程数。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|跳过指定的枚举序列中的线程数。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|将枚举序列重置到开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|创建包含当前与相同的枚举状态的枚举。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|获取枚举器中的线程数。|  
  
## <a name="remarks"></a>备注  
 Visual Studio 通常将获取此接口可更新**线程**窗口以及有关获取要调用的列表中，在第一个线程[执行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)，[继续](../../../extensibility/debugger/reference/idebugprocess3-continue.md)，和[步骤](../../../extensibility/debugger/reference/idebugprocess3-step.md)。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [步骤](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [继续](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [执行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)