---
title: "Ijsdebugdatatarget:: Gettlsvalue 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4205adfb24a1a64d4e90f3fdcaf5a5ecbc4028de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue 方法
有关正在调试的线程，检索指定的 TLS 索引的线程本地存储 (TLS) 槽中的值。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>参数  
 `threadId`  
 [in]在要从其中进行读取目标进程中运行的线程。  
  
 `tlsIndex`  
 [in]目标进程调用 TlsAlloc 函数时已分配 TLS 索引。  
  
 `pValue`  
 [out]指针大小的值已存储在线程的 TLS 槽。 如果目标线程是 32 位，此值的高 32 位将为零。  
  
## <a name="return-value"></a>返回值  
  
## <a name="remarks"></a>备注  
 进程的每个线程具有其自己为每个 TLS 索引槽。  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>另请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)