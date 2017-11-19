---
title: "IDebugMemoryBytes2::ReadAt |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4de46d516efca856deef6fa9070e466de73e258f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
读取给定位置开始的字节序列。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pStartContext`  
 [in][IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)对象，它指定从何处着手读取的字节。  
  
 `dwCount`  
 [in]要读取的字节数。 此外指定的长度`rgbMemory`数组。  
  
 `rgbMemory`  
 [在中，out]实际读取使用字节填充的数组。  
  
 `pdwRead`  
 [out]返回实际读取的连续字节数。  
  
 `pdwUnreadable`  
 [在中，out]返回不可读字节的数。 如果客户端不愿意中的不可读字节数，则可能是一个 null 值。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 如果请求 100 个字节前 50 个是否都可读下, 一步 20 是不可读取的和剩余 30 台可读，则此方法返回：  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 在这种情况下，因为`*pdwRead + *pdwUnreadable < dwCount`，调用方必须进行额外调用读取请求的原始 100 剩余 30 字节和[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)传入的对象`pStartContext`必须高级参数通过 70。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)