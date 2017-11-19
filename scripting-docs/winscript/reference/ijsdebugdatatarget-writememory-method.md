---
title: "Ijsdebugdatatarget:: Writememory 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed562c1cbdd645da6cca87e45f272c25f8bc0d4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory 方法
读取目标进程的内存。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>参数  
 `address`  
 [in]从中写入目标进程的内存基址。  
  
 `pMemory`  
 [in]要写入指定的进程的地址空间中的数据。  
  
 `size`  
 [in]要写入到进程的字节数。  
  
## <a name="return-value"></a>返回值  
  
## <a name="remarks"></a>备注  
 数据传输发生之前，系统将验证的基址和指定大小的内存中的所有数据以进行写访问，可访问，并且如果它是不可访问，该函数将引发 E_JsDEBUG_INVALID_MEMORY_ADDRESS 错误。  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>另请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)