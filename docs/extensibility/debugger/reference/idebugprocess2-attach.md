---
title: "IDebugProcess2::Attach |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::Attach
helpviewer_keywords: IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 840f2dee6648a84b0f7c6259049dcc701b5aef82
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
将会话调试管理器 (SDM) 附加到进程。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)调试事件通知使用的对象。  
  
 `rgguidSpecificEngines`  
 [in]可用于调试在进程中运行的程序的调试引擎的 Guid 数组。 此参数可以为 null 值。 有关详细信息，请参阅备注。  
  
 `celtSpecificEngines`  
 [in]调试数引擎中`rgguidSpecificEngines`数组和大小`rghrEngineAttach`数组。  
  
 `rghrEngineAttach`  
 [在中，out]HRESULT 代码的调试引擎返回的数组。 此数组的大小以指定`celtSpecificEngines`参数。 每个代码是通常`S_OK`或`S_ATTACH_DEFERRED`。 后者，则指示 DE 当前连接到任何节目。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。 下表显示其他可能的值。  
  
|值|描述|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定的进程已附加到调试器中。|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|附加过程中发生了安全冲突。|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|桌面进程无法附加到调试器。|  
  
## <a name="remarks"></a>备注  
 附加到进程将 SDM 附加到运行中指定的调试引擎 (DE) 可以调试该进程中的所有程序`rgguidSpecificEngines`数组。 设置`rgguidSpecificEngines`为 null 的参数值，或将包括`GUID_NULL`数组中要将附加到进程中的所有程序。  
  
 在进程中发生的所有调试事件都发送到给定[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)对象。 这`IDebugEventCallback2`SDM 调用此方法时提供对象。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)