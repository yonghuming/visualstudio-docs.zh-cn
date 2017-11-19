---
title: "DISASSEMBLY_STREAM_SCOPE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords: DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9cbd0ea73c7efea5cee570548dec5570ffc53b42
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
指定反汇编流作用的域。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>成员  
 DSS_HUGE  
 指定反汇编的代码上下文会生成更多输出不是客户端通常想要在单个调用中检索。  
  
 DSS_FUNCTION  
 指定应反汇编的代码上下文所包含的函数。 指定反汇编流表示一个函数，返回时[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)方法。  
  
 DSS_MODULE  
 返回时`IDebugDisassemblyStream2::GetScope`方法，指定反汇编流表示一个模块。  
  
 DSS_ALL  
 指定的整个地址空间的反汇编。  
  
## <a name="remarks"></a>备注  
 作为自变量传递[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)方法并返回[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)方法。  
  
 这些值可以与按位组合`OR`。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)