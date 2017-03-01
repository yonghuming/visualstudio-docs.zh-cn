---
title: "IDebugReference2::GetDerivedMostReference |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 10
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
ms.openlocfilehash: 1cb281e93eb462de607f83a4e1d2d72785cef9a2
ms.lasthandoff: 02/22/2017

---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
获取派生程度最大引用的引用。 留待将来使用。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppDerivedMost`  
 [out]返回[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)表示派生程度最高属性的对象。  
  
## <a name="return-value"></a>返回值  
 始终返回 `E_NOTIMPL`。  
  
## <a name="remarks"></a>备注  
 例如，如果此属性描述实现的对象`ClassRoot`，但这是实际的实例化`ClassDerived`派生自`ClassRoot`，则此方法返回[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)对象，表示对引用`ClassDerived`对象。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
