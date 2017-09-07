---
title: "BP_FLAGS90 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5e958be77ca266af30556fa8c03c580eea94b903
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="bpflags90"></a>BP_FLAGS90
枚举有效可选标志的值。 可选标志可能用于设置断点时指定的其他信息。 此枚举扩展[BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)枚举。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>参数  
 BP90_FLAG_NONE  
 不指定任何断点标志。  
  
 BP90_FLAG_MAP_DOCPOSITION  
 指定的调试引擎 (DE) 应通过使用文档位置映射断点。 这是仅适用于面向脚本的源代码文件，如 Active Server Pages (ASP) 中设置断点。  
  
 BP90_FLAG_DONT_STOP  
 指定的调试引擎中，应处理断点，但调试引擎最终应不停止进行控制。也就是说， [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)不应发送事件对象。 此标志用于主要与跟踪点一起使用。  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 由本机调试引擎使用，以确定是否应清除单步执行状态。 它不同于 BP90_FLAG_DONT_STOP 因为如果跟踪点执行宏，则不会设置 BP90_FLAG_DONT_STOP 的不同而不同。  
  
## <a name="requirements"></a>要求  
 标头： Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
