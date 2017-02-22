---
title: "IDebugProgramEx2::Attach | Microsoft Docs"
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
  - "IDebugProgramEx2::Attach"
helpviewer_keywords: 
  - "IDebugProgramEx2::Attach"
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

附加会话进行编程。  
  
## 语法  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### 参数  
 `pCallback`  
 \[in\] 表示回调函数的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 对象附加的调试引擎发送事件。  
  
 `dwReason`  
 \[in\] 从描述附加操作的原因的 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) 枚举的值。  
  
 `pSession`  
 \[in\] 唯一标识会话附加到程序的值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  ，如果程序已附加属性，此方法应返回 `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` 。  
  
## 备注  
 包含程序的端口。 `pSession` 可以使用该值确定哪个会话尝试附加到程序。  例如，如果端口，只允许一个调试会话一次附加到进程，端口可以确定同一会话是否已附加到进程中的其他程序。  
  
> [!NOTE]
>  在 `pSession` 传递的接口将只视为 cookie，唯一标识该会话调试附加到此过程的管理器的值;在提供的接口的任何方法都不起作用。  
  
## 请参阅  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)