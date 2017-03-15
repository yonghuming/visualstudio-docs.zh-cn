---
title: "EXCEPTION_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_STATE"
helpviewer_keywords: 
  - "EXCEPTION_STATE 枚举"
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定异常状态。  
  
## 语法  
  
```cpp#  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```c#  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## 成员  
 EXCEPTION\_NONE  
 不要停止在异常。  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE  
 停止在异常第一个激发。  当描述异常事件时，该标志指示异常事件是首次异常事件。  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE  
 停止在异常第二激发。  当描述异常事件时，指示异常事件是一个第二次异常事件。  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE  
 停止在用户模式异常的第一个激发。  当描述异常事件时，指示异常事件是首次用户异常事件。  
  
 EXCEPTION\_STOP\_USER\_UNCAUGHT  
 ，当用户模式异常未捕获，请停止。  当描述异常事件时，指示异常事件是在用户模式异常事件。  
  
 EXCEPTION\_STOP\_ALL  
 停止对所有异常。  不使用，当描述异常事件时。  
  
 不是 EXCEPTION\_CAN \_BE\_CONTINUED  
 当描述异常事件时，指示异常无法继续。  
  
 EXCEPTION\_CODE\_SUPPORTED  
 指示异常对于支持它的代码。  使用在显示异常  
  
 EXCEPTION\_CODE\_DISPLAY\_IN\_HEX  
 指示在十六进制应显示异常代码。  使用在显示异常。  
  
 EXCEPTION\_JUST\_MY\_CODE\_SUPPORTED  
 指示异常代码支持 JustMyCode。  使用在显示异常。  
  
 EXCEPTION\_MANAGED\_DEBUG\_ASSISTANT  
 如果处理异常，指示托管代码调试器。  如果未设置，默认调试器处理异常。  这是通过对 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) 方法和不使用 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) 结构。  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE\_USE\_PARENT  
 过时，不要使用。  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE\_USE\_PARENT  
 过时，不要使用。  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE\_USE\_PARENT  
 过时，不要使用。  
  
 EXCEPTION\_STOP\_USER\_SECOND\_CHANCE\_USE\_PARENT  
 过时，不要使用。  
  
## 备注  
 用于为 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) 结构的 `dwState` 成员指示异常状态，并可对该执行。  
  
 这些值来传递给 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) 方法将所有异常状态。  
  
 这些标志可以按位组合使用或。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)