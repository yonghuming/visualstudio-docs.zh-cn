---
title: "IDebugMemoryBytes2::WriteAt |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 14d5aa4fa026f27f6b083d656cd5df3f8b7d7f41
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
写入指定的内存，从指定地址开始的字节数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pStartContext`  
 [in][IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)对象，它指定从何处着手写入字节。  
  
 `dwCount`  
 [in]要写入的字节数。  
  
 `rgbMemory`  
 [in]要写入的字节。 此数组被假定为至少`dwCount`大小中的字节数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回`S_FALSE`如果不是所有字节无法编写或返回错误代码 (通常`E_FAIL`)。  
  
## <a name="remarks"></a>备注  
 如果起始地址不在此所表示的内存窗口[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)对象时，发生任何写操作和错误代码的`E_FAIL`返回 — 即使要写入的量重叠到内存空间。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
