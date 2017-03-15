---
title: "DISASSEMBLY_STREAM_SCOPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_STREAM_SCOPE"
helpviewer_keywords: 
  - "DISASSEMBLY_STREAM_SCOPE 枚举"
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定反汇编流的大小。  
  
## 语法  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## 成员  
 DSS\_HUGE  
 比客户端在单个通常需要检索调用指定反汇编代码的上下文将生成多个输出。  
  
 DSS\_FUNCTION  
 指定应反汇编代码上下文包含的功能。  指定反汇编流表示函数，那么，当返回的 [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md) 方法。  
  
 DSS\_MODULE  
 当返回的 `IDebugDisassemblyStream2::GetScope` 方法，指定要反汇编流表示模块。  
  
 DSS\_ALL  
 为整个地址空间指定反汇编。  
  
## 备注  
 将作为参数传递 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) 方法和返回的 [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md) 方法。  
  
 这些值可能按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)