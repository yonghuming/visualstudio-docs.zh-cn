---
title: "IDebugMemoryContext2::Compare |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dbcb3f93a4db6a14775cfe518ed257e60282f1fb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
比较每个上下文中指示由比较标志，返回与匹配的第一个上下文的索引的方式与给定数组中的内存上下文。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```csharp  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### <a name="parameters"></a>参数  
 `compare`  
 [in]取值范围为[CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)确定的比较类型的枚举。  
  
 `rgpMemoryContextSet`  
 [in]对引用的数组[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)要比较的对象。  
  
 `dwMemoryContextSetLen`  
 [in]中的上下文数`rgpMemoryContextSet`数组。  
  
 `pdwMemoryContext`  
 [out]返回满足的比较的第一个内存上下文的索引。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。 返回`E_COMPARE_CANNOT_COMPARE`如果两个上下文不能进行比较。  
  
## <a name="remarks"></a>备注  
 调试引擎 (DE) 不需要支持所有类型的比较，但它必须至少都支持`CONTEXT_EQUAL`， `CONTEXT_LESS_THAN`，`CONTEXT_GREATER_THAN`和`CONTEXT_SAME_SCOPE`。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)