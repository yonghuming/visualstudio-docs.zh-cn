---
title: "JsDebugReadMemoryFlags 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7efb5170bf0314e95b1acded39a897c2236a29ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>JsDebugReadMemoryFlags 枚举
读取内存时用于指定行为的标志。  
  
## <a name="syntax"></a>语法  
  
```  
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>成员  
  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|指示调用方想要成功如果仅内存的一部分读取成功的读取的操作。 如果此设置，如果地址无效，将只会引发 E_JsDEBUG_INVALID_MEMORY_ADDRESS 错误。 如果清除此标志，如果请求的任何的内存部分是不可读，将会引发 E_JsDEBUG_INVALID_MEMORY_ADDRESS 错误。|  
|`None`|指示调用方为 ReadMemory 想默认行为。|  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>另请参阅  
 [Windows 脚本接口参考](../../winscript/reference/windows-script-interfaces-reference.md)