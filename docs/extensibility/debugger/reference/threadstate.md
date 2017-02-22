---
title: "THREADSTATE | Microsoft Docs"
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
  - "THREADSTATE"
helpviewer_keywords: 
  - "THREADSTATE 枚举"
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# THREADSTATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定线程的状态。  
  
## 语法  
  
```cpp#  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```c#  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## 成员  
 THREADSTATE\_RUNNING  
 指示线程上运行。  
  
 THREADSTATE\_STOPPED  
 指示由于断点，线程终止。  
  
 THREADSTATE\_FRESH  
 指示线程创建的，则，但不运行代码。  
  
 THREADSTATE\_DEAD  
 指示线程处于不活动状态。  
  
 THREADSTATE\_FROZEN  
 指示线程已冻结 \(执行不能执行\)。  
  
## 备注  
 用于 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) 结构的 `dwThreadState` 字段。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)