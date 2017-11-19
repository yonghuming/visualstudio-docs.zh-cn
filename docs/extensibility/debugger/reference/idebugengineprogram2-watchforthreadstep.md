---
title: "IDebugEngineProgram2::WatchForThreadStep |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords: IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 473deca83bea9e2fea9c52d2836291790def5804
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
监视的执行 （或停止监视执行） 的给定线程上发生。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```csharp  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pOriginatingProgram`  
 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)代表正在单步执行该程序的对象。  
  
 `dwTid`  
 [in]指定要监视的线程的标识符。  
  
 `fWatch`  
 [in]非零 (`TRUE`) 意味着启动监视由线程执行`dwTid`; 否则为零 (`FALSE`) 意味着停止上观看执行`dwTid`。  
  
 `dwFrame`  
 [in]指定一个帧索引，它控制的步骤类型。 在这种值为零 (0)、 步骤类型是"单步执行"和该程序应停止线程的标识出由`dwTid`执行。 当`dwFrame`为非零，步骤类型是"逐过程"，并且仅当线程由标识，该程序应停止`dwTid`运行中的索引是等于或更高版本比堆栈上某个帧`dwFrame`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 当会话调试管理器 (SDM) 步骤的程序，由标识`pOriginatingProgram`参数，它将通知所有其他附加的程序通过调用此方法。  
  
 此方法是仅适用于同一线程单步执行。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)