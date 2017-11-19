---
title: "IDebugProgram2::Execute |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Execute
helpviewer_keywords: IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: be6a1f1b2259b573b829490d6015eb1964790679
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
将继续从停止的状态运行此程序。 清除任何以前的执行状态 （如步骤），并在程序启动再次执行。  
  
> [!NOTE]
>  此方法已弃用。 使用[执行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)方法相反。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 当用户开始从停止状态在某些其他程序的线程中执行时，在此程序上调用此方法。 当用户选择，则还会调用此方法**启动**命令**调试**菜单在 IDE 中的。 此方法的实现可能很简单，只需与调用[恢复](../../../extensibility/debugger/reference/idebugthread2-resume.md)在程序中当前线程上的方法。  
  
> [!WARNING]
>  不发送 stopping 事件或即时 （同步） 事件与[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)时处理此调用; 否则调试器可能会挂起。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)