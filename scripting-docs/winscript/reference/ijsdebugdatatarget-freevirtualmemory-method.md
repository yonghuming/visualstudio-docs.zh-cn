---
title: "Ijsdebugdatatarget:: Freevirtualmemory 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b53d7f80227a1c4eb0ef0293093543c09c5a367
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory 方法
释放和/或解除的目标进程的虚拟地址空间中的内存区域。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>参数  
 `address`  
 [in]在目标进程应释放内存内地址。  
  
 `size`  
 [in]要解除的字节数。 若要释放的内存区域，此值必须为零。  
  
 `freeType`  
 [in]指示要执行的可用操作的类型。 这通常是 MEM_RELEASE (0x8000) 释放页指定的区域。 操作后，这些页将处于可用状态。 可以改为使用 MEM_DECOMMIT (0x4000)，以解除页，而不释放它们。  
  
## <a name="return-value"></a>返回值  
  
## <a name="remarks"></a>备注  
 有关其他信息，请参阅 VirtualFree Win32 API。  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>另请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)