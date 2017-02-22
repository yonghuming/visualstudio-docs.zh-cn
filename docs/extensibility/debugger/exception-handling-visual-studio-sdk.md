---
title: "异常处理 (Visual Studio SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，异常处理"
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 异常处理 (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下面描述发生的处理，引发异常时。  
  
## 异常处理  
  
1.  如果异常是第一个引发时，，但是，在使用之前正在调试的程序的异常处理程序，调试引擎 \(DE\)发送 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 到该会话调试管理器 \(SDM\)作为一个停止点的事件。  发送 `IDebugExceptionEvent2` ，如果异常的仅设置 \(指定在调试包的异常对话框\) 指定用户在首次异常通知若要停止。  
  
2.  SDM 调用 [IDebugExceptionEvent2:: GetException](../Topic/IDebugExceptionEvent2::GetException.md) 捕获异常属性。  
  
3.  调试打包名为 [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 确定存在的任何选项给用户。  
  
4.  调试包如何请求用户处理异常通过打开首次异常对话框。  
  
5.  如果用户选择继续， SDM 调用 [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)。  
  
    -   如果该方法将返回 S\_OK，调用 [IDebugExceptionEvent2:: PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)。  
  
         \- 或 \-  
  
         如果此方法返回 S\_FALSE，正在调试的程序给第二次机会处理异常。  
  
6.  如果正在调试的程序没有第二次异常的处理程序， DE 发送 `IDebugExceptionEvent2` 到 SDM 作为 **EVENT\_SYNC\_STOP**。  
  
7.  调试包如何请求用户处理异常通过打开首次异常对话框。  
  
8.  调试打包名为 [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 确定存在的任何选项给用户。  
  
9. 调试包如何请求用户处理异常通过打开是第二次异常对话框。  
  
10. 如果该方法将返回 S\_OK，调用 `IDebugExceptionEvent2::PassToDebuggee`。  
  
## 请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)