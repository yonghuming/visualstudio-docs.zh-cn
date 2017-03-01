---
title: "IDebugObject::IsNullReference |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
caps.latest.revision: 9
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8dc2376af276a99dd63bbc4d4ffd89825acc1762
ms.lasthandoff: 02/22/2017

---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
测试此对象是否为空引用。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```c#  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pfIsNull`  
 [out]返回非零值 (`TRUE`) 如果此对象为空引用; 否则，返回零 (`FALSE`)。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 空引用意味着一个空的对象或未分配给对象。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
