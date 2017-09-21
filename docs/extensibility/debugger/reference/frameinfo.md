---
title: "FRAMEINFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FRAMEINFO"
helpviewer_keywords: 
  - "FRAMEINFO 结构"
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# FRAMEINFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述一个堆栈帧。  
  
## 语法  
  
```cpp#  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```c#  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## 成员  
 m\_dwValidFields  
 标志的组合从指定的 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) 枚举的哪些字段填充。  
  
 m\_bstrFuncName  
 函数名与堆栈帧。  
  
 m\_bstrReturnType  
 返回类型与堆栈帧。  
  
 m\_bstrArgs  
 函数的参数与堆栈帧。  
  
 m\_bstrLanguage  
 函数实现的语言。  
  
 m\_bstrModule  
 模块名称与堆栈帧。  
  
 m\_addrMin  
 最小的实际堆栈地址。  
  
 m\_addrMAX  
 最大物理堆栈地址。  
  
 m\_pFrame  
 表示此堆栈帧的 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 对象。  
  
 m\_pFrame  
 表示模块包含此堆栈帧的 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 对象。  
  
 m\_fHasDebugInfo  
 非零 \(`TRUE`\)，如果调试信息存在于特定框架。  
  
 m\_fHasDebugInfo  
 非零 \(`TRUE`\)，如果堆栈帧与不再有效的代码。  
  
 m\_fHasDebugInfo  
 非零 \(`TRUE`\)，如果堆栈帧由会话批注的调试管理器 \(SDM\)。  
  
## 备注  
 此结构传递给将填充的 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) 方法。  此机制在 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 接口包含在调用，然后，返回到 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 方法的列表还包含。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)