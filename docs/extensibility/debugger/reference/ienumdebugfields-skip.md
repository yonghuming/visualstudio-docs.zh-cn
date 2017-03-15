---
title: "IEnumDebugFields::Skip |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugFields::Skip
helpviewer_keywords:
- IEnumDebugFields::Skip method
ms.assetid: b3bc51c4-21ae-4913-800c-c2ca9dc18443
caps.latest.revision: 7
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
ms.openlocfilehash: 2174206faa86e9853bcc31f1f91add9361f00636
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugfieldsskip"></a>IEnumDebugFields::Skip
此方法同时跳过指定数量的元素。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>参数  
 `celt`  
 [in]要跳过的元素数。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回`S_OK`。 返回`S_FALSE`如果`celt`超过了剩余的元素数; 否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 如果`celt`指定的值超出指定数量的剩余元素的枚举设置为结束和`S_FALSE`返回。  
  
## <a name="see-also"></a>另请参阅  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
