---
title: "Ijsdebugdatatarget:: Readmemory 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1b67b33e17761a675d6ced9e175b4206ede2e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory 方法
读取目标进程的内存。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>参数  
 `address`  
 [in]要从其中读取目标进程的内存基址。  
  
 `flags`  
 [in]控制 ReadMemory 行为的标志。  
  
 `pBuffer`  
 [out]用于接收缓冲区的内容从目标进程的地址空间。 在失败时，此缓冲区的内容是未指定。  
  
 `size`  
 [in]要从过程中读取的字节数。  
  
 `pBytesRead`  
 [out]指示从目标进程中读取的字节数。 如果清除了 JsDebugAllowPartialRead，成功此值将始终为完全等于输入的大小。 如果指定 JsDebugAllowPartialRead，成功时，此值将大于零。  
  
## <a name="return-value"></a>返回值  
  
## <a name="remarks"></a>备注  
 返回，则为 S_OK 成功和失败代码上的使用的任何错误。 如果的地址不是有效，返回 E_JsDEBUG_INVALID_MEMORY_ADDRESS。 有关详细信息，请参阅 JsDebugAllowPartialRead。  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>另请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)