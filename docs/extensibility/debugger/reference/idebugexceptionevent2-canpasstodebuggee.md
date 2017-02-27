---
title: "IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::CanPassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::CanPassToDebuggee"
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

确定是否 \(DE\)调试引擎通过此异常的选项传递给正在调试的程序，当执行恢复。  
  
## 语法  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```c#  
int CanPassToDebuggee();  
```  
  
## 返回值  
 返回 `S_OK` \(异常可以传递给程序\) 或 `S_FALSE` \(异常不能传递\)。  
  
## 备注  
 DE 必须通过的默认事件与调试对象。  IDE 会接收 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 事件和调用 [继续](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 方法，而不调用 `CanPassToDebuggee` 方法。  因此， DE 应具有传递的异常默认大小写。  
  
## 请参阅  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [继续](../../../extensibility/debugger/reference/idebugprocess3-continue.md)