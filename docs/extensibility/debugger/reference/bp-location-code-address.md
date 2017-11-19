---
title: "BP_LOCATION_CODE_ADDRESS |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_CODE_ADDRESS
helpviewer_keywords: BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0dc53f11dd4ba06488dbd53b9a1f4014268412d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="bplocationcodeaddress"></a>BP_LOCATION_CODE_ADDRESS
描述在代码中的一个地址断点的位置。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef struct _BP_LOCATION_CODE_ADDRESS {   
   BSTR bstrContext;  
   BSTR bstrModuleUrl;  
   BSTR bstrFunction;  
   BSTR bstrAddress;  
} BP_LOCATION_CODE_ADDRESS;  
```  
  
## <a name="members"></a>成员  
 `bstrContext`  
 断点的上下文，通常一个方法或函数的名称，作为调用堆栈上看到。  
  
 `bstrModuleUrl`  
 包含断点的模块的 URL。  
  
 `bstrFunction`  
 包含断点的函数的名称。  
  
 `bstrAddress`  
 断点，该表达式计算器才能将其绑定到的分析的地址[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)对象。  
  
## <a name="remarks"></a>备注  
 此结构是的成员[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)作为联合的一部分的结构。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)