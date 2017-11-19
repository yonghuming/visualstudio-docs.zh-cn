---
title: "EXCEPTION_STATE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EXCEPTION_STATE
helpviewer_keywords: EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6237e061028ad568c0fdc0ed344d9eb86300c463
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
指定的异常状态。  
  
## <a name="syntax"></a>语法  
  
```cpp  
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
  
```csharp  
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
  
## <a name="members"></a>成员  
 EXCEPTION_NONE  
 不在的异常处停止。  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 在第一个激发的异常处停止。 描述异常事件时, 此标志指示的异常事件是首次异常事件。  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 在第二个触发异常处停止。 描述异常事件，指示异常事件是第二次异常事件。  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 在第一个激发的用户模式异常处停止。 描述异常事件，指示异常事件是第一个可能的用户异常事件。  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 在用户模式异常未被捕获时停止。 描述异常事件，指示异常事件是未捕获的用户模式异常事件。  
  
 EXCEPTION_STOP_ALL  
 停止任何异常。 描述异常事件时，不使用。  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 描述异常事件，指示异常不能继续从。  
  
 EXCEPTION_CODE_SUPPORTED  
 指示异常具有支持它的代码。 用于显示异常  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 指示应以十六进制格式显示该异常代码。 在显示异常中使用。  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 指示的异常代码支持 JustMyCode。 在显示异常中使用。  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 指示托管的代码调试程序应处理异常。 如果未设置，默认调试器将处理异常。 这将传递到[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)方法而不用于[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)结构。  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 过时，则不要使用。  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 过时，则不要使用。  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 过时，则不要使用。  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 过时，则不要使用。  
  
## <a name="remarks"></a>备注  
 用作`dwState`的成员[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)结构来指示的异常，无法完成有关它的状态。  
  
 这些值也将传递给[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)方法用于设置状态的所有异常。  
  
 可能与按位 OR 组合这些标志。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)