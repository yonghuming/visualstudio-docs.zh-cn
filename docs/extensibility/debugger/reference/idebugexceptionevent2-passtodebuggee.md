---
title: "IDebugExceptionEvent2::PassToDebuggee |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords: IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4abb59c9bf9717089353683087c38425d3bf88ed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
指定异常应该传递到如果执行恢复，被调试的程序是否应放弃该异常。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>参数  
 `fPass`  
 [in]非零 (`TRUE`) 如果异常应该传递到如果执行恢复，被调试的程序或零 (`FALSE`) 如果应放弃该异常。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 调用此方法不实际上会导致在正在调试的程序中执行的任何代码。 调用只是用于设置下一步执行代码的状态。 例如，调用[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)方法可能返回`S_OK`与[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)。`dwState` 字段设置为`EXCEPTION_STOP_SECOND_CHANCE`。  
  
 IDE 可能会收到[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)事件并调用[继续](../../../extensibility/debugger/reference/idebugprogram2-continue.md)方法。 调试引擎 (DE) 应具有一个默认行为以处理情况`PassToDebuggee`不调用方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)