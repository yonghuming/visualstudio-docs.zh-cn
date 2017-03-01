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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4dfb7dc681519b37fe5cb9cd20e4bca22d800b96
ms.lasthandoff: 02/22/2017

---
# <a name="bpflags90"></a>BP_FLAGS90
枚举的有效值可选标志。 可选标志可能用于设置断点时指定的其他信息。 此枚举扩展[BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)枚举。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
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
  
```c#  
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
 指定的调试引擎 (DE) 应通过使用文档位置映射断点。 这是仅适用于面向脚本的源代码文件，如 Active Server Pages (ASP) 中设置的断点。  
  
 BP90_FLAG_DONT_STOP  
 指定调试引擎中，应处理断点，但是，调试引擎最终应停止控制。也就是说， [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)不应发送事件对象。 此标志用于主要与跟踪点一起使用。  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 由本机调试引擎用于确定是否应该清除单步执行状态。 它不同于 BP90_FLAG_DONT_STOP 因为如果跟踪点执行宏，则不设置 BP90_FLAG_DONT_STOP。  
  
## <a name="requirements"></a>要求  
 标头︰ Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
