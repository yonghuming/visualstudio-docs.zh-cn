---
title: "IDebugProcess2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::Attach"
helpviewer_keywords: 
  - "IDebugProcess2::Attach"
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

附加会议调试管理器 \(SDM\)到进程。  
  
## 语法  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### 参数  
 `pCallback`  
 \[in\] 使用的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 对象的调试事件通知。  
  
 `rgguidSpecificEngines`  
 \[in\] 数组 GUID 调试要使用的引擎调试运行在处理过程。  此参数可以为空值。  请参见 " 备注 " 了解详细信息。  
  
 `celtSpecificEngines`  
 \[in\] 数字调试在 `rgguidSpecificEngines` 和 `rghrEngineAttach` 数组大小的引擎。  
  
 `rghrEngineAttach`  
 \[in, out\] HRESULT 代码的调试引擎返回。  此数组的大小 `celtSpecificEngines` 参数指定。  每个代码通常是 `S_OK` 或 `S_ATTACH_DEFERRED`。  后者指示、当前附加到不程序。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  下表显示其他可能的值。  
  
|值|说明|  
|-------|--------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定的进程已附加到调试器。|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|在附加过程中，安全违规发生。|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|桌面进程无法附加到调试器。|  
  
## 备注  
 附加到进程附加 SDM 到运行由于可以由 `rgguidSpecificEngines` 数组指定的调试引擎 \(DE\)调试的所有程序的过程。  设置 `rgguidSpecificEngines` 参数设置为空值或包含 `GUID_NULL` 在数组附加到进程中的所有程序。  
  
 所有调试在过程将发送到特定 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 对象的事件。  此 `IDebugEventCallback2` 对象，而 SDM 调用此方法时，提供。  
  
## 请参阅  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)