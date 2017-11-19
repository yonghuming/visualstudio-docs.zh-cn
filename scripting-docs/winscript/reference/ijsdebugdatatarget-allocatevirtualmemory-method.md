---
title: "Ijsdebugdatatarget:: Allocatevirtualmemory 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.AllocateVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65b29bbf9a3405bcfab779bd877f798a863538d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory 方法
保留和/或提交目标进程的虚拟地址空间中的内存区域。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>参数  
 `address`  
 [in]在目标进程中应提交或保留的内存地址。 此值通常为的零，在该情况下，系统选择地址。  
  
 `size`  
 [in]要分配，以字节为单位的内存区域的大小。 系统将自动向上舍入为下一步的页边界。  
  
 `allocationType`  
 [in]指示用于执行分配的类型。 这通常是 MEM_COMMIT &#124;MEM_RESERVE (0x3000) 也不能保留提交分配在一个步骤。  
  
 `pageProtection`  
 [in]页面，并将其分配的内存保护区域。 如果正在提交页，可以指定内存保护常量 （例如，PAGE_READWRITE，PAGE_EXECUTE） 之一。  
  
 `pAllocatedAddress`  
 [out]页的已分配区域的基址。  
  
## <a name="return-value"></a>返回值  
  
## <a name="remarks"></a>备注  
 除非使用 MEM_RESET，该函数将初始化为零，它分配的内存。 有关其他信息，请参阅 VirtualAlloc Win32 API。  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>另请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)