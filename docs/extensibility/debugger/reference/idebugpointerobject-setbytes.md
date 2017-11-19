---
title: "IDebugPointerObject::SetBytes |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerObject::SetBytes
helpviewer_keywords: IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91e11f0e321e286eaf669b50d2fa564fa29df314
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
设置从一系列连续字节指向的值。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwStart`  
 [in]偏移量，以字节为单位的开始处指向的对象。  
  
 `dwCount`  
 [in]要设置的字节数。  
  
 `pBytes`  
 [in]表示新值的字节数组。 此值将存储到的对象，从给定的偏移量处开始。  
  
 `pdwBytes`  
 [out]返回实际设置的字节数。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 如果使用此方法的指针所表示的这[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)指向基元类型或基元类型 （即，可以通过简单的序列的字节来表示一个数组） 的简单的数组。 这`IDebugPointerObject`对象不能为空引用 （它必须指向出现在内存中的地址）。  
  
## <a name="see-also"></a>另请参阅  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)