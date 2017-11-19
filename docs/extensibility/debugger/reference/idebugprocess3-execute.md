---
title: "IDebugProcess3::Execute |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::Execute
helpviewer_keywords: IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96b18bdb8aa0097071369a01013772dc3bd0d5bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
将继续运行此过程从已停止状态。 清除任何以前的执行状态 （如步骤） 和进程启动再次执行。  
  
> [!NOTE]
>  此方法应使用而不是[执行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)对象表示要执行的线程。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 当用户开始从停止状态在某些其他进程的线程中执行时，在此过程上调用此方法。 当用户选择，则还会调用此方法**启动**命令**调试**菜单在 IDE 中的。 此方法的实现可能很简单，只需与调用[恢复](../../../extensibility/debugger/reference/idebugthread2-resume.md)过程中在当前线程上的方法。  
  
> [!WARNING]
>  不发送 stopping 事件或即时 （同步） 事件与[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)时处理此调用; 否则调试器可能会挂起。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [恢复](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)