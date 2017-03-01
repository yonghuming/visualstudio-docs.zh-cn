---
title: "IDebugProperty2::GetMemoryBytes |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty2::GetMemoryBytes
helpviewer_keywords:
- IDebugProperty2::GetMemoryBytes
ms.assetid: b32042ed-7a06-4b4a-99ef-fe03b0aa61cc
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
ms.openlocfilehash: 52208276b8e2ca2d6fd7f98b0b497a6c7b237c31
ms.lasthandoff: 02/22/2017

---
# <a name="idebugproperty2getmemorybytes"></a>IDebugProperty2::GetMemoryBytes
获取构成一个属性的值的内存字节数。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetMemoryBytes (   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```c#  
int GetMemoryBytes (   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppMemoryBytes`  
 [out]返回[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)可以用于检索包含属性的值的内存的对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回`S_OK`; 否则返回错误代码。 返回`S_GETMEMORYBYTES_NO_MEMORY_BYTES`是否存在任何内存的字节数来检索。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
