---
title: "BP_LOCATION_DATA_STRING |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_DATA_STRING
helpviewer_keywords: BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7952392b55f351332ba8163fe1bd4c04c3883d87
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
用于设置数据断点基于用户可以输入从集成的开发环境 (IDE) 的字符串。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## <a name="members"></a>成员  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)表示断点发生时所在的线程的对象。  
  
 `bstrContext`  
 在代码中的断点，通常一个方法或函数的名称，作为调用堆栈上看到的上下文。  
  
 `bstrDataExpr`  
 数据字符串对用户进行输入，若要设置断点。  
  
 `dwNumElements`  
 发生断点所在的数据字符串中的元素数。  
  
## <a name="remarks"></a>备注  
 此结构是的成员[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)作为联合的一部分的结构。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)