---
title: "ATTACH_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATTACH_REASON"
helpviewer_keywords: 
  - "ATTACH_REASON 枚举"
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# ATTACH_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定其原因以便调试引擎 \(DE\)可以附加到程序节点。  
  
## 语法  
  
```cpp#  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```c#  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## 成员  
 ATTACH\_REASON\_AUTO  
 ，因为该进程是当前调试模式，请附加。  
  
 ATTACH\_REASON\_LAUNCH  
 ，因为该进程已生成了，则附加。  
  
 ATTACH\_REASON\_USER  
 由于用户请求，附加。  
  
## 备注  
 这些值用作 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 和 [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) 方法的参数。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)