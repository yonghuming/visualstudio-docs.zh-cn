---
title: "DEBUG_REASON |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_REASON
helpviewer_keywords: DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9607afd765e1ddbc9fb2be97a0b7694aed7d493d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debugreason"></a>DEBUG_REASON
指定原因为调试启动进程。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>参数  
 DEBUG_REASON_ERROR  
 非特定错误发生 （这作为默认条件时使用的另一个原因适合）。  
  
 DEBUG_REASON_USER_LAUNCHED  
 在用户的请求时启动该过程。  
  
 DEBUG_REASON_USER_ATTACHED  
 已运行的进程已附加到用户。  
  
 DEBUG_REASON_AUTO_ATTACHED  
 程序启动时，该过程已自动附加到。  
  
 DEBUG_REASON_CAUSALITY  
 由于启动进程*中实时*(JIT) 调试事件。  
  
## <a name="remarks"></a>备注  
 返回从[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)方法。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)