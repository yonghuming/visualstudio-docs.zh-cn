---
title: "BP_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_FLAGS"
helpviewer_keywords: 
  - "BP_FLAGS 枚举"
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

提供可用于指定附加信息，当设置断点时的可选标志。  
  
## 语法  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```c#  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## 成员  
 BP\_FLAG\_NONE  
 未指定断点标志。  
  
 BP\_FLAG\_MAP\_DOCPOSITION  
 指定使用文档位置，调试引擎 \(DE\)应映射断点。  这只适用于脚本面向源文件设置的断点例如 Active Server Page \(ASP\)。  
  
 不是 BP\_FLAG\_DO \_STOP  
 指定应由调试引擎处理断点，但是，调试引擎不应最终停止其中 \(不应发送即 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 事件对象\)。  此标志的设计初衷是主要与跟踪点。  
  
## 备注  
 用于 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 和 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 结构的 `dwFlags` 成员。  
  
 这些值可能按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)