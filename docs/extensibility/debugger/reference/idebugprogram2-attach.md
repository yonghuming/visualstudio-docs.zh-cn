---
title: "IDebugProgram2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Attach"
helpviewer_keywords: 
  - "IDebugProgram2::Attach"
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

附加到程序。  
  
## 语法  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### 参数  
 `pCallback`  
 \[in\] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 对象将用于调试事件通知。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  下表显示一些可能的错误代码。  
  
|值|说明|  
|-------|--------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定的程序已附加到调试器。|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|在附加过程中，安全违规发生。|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|桌面程序无法附加到调试器。|  
  
## 备注  
 调试引擎 \(DE\)从不调用此方法附加到程序。  如果 DE 在程序地址空间运行， [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 方法调用。  如果 DE 在会话中运行调试管理器的地址空间 \(SDM\)， [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法调用。  
  
## 请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)