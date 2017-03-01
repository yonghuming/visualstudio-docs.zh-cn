---
title: "IPropertyProxyEESide::InPlaceUpdateObject |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 11
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
ms.openlocfilehash: f07bc5831a0c25d4006005dd2c97af0ec111559a
ms.lasthandoff: 02/22/2017

---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
更新与给定的数据对象的对象的数据并返回一个新的数据对象，表示对象的新数据。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```c#  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dataIn`  
 [in][IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)对象，其中包含新的数据。  
  
 `dataOut`  
 [out]返回一个新`IEEDataStorage`对象，其中包含被替换的数据。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 此方法实际上更新对象的数据。 在返回的数据[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)对象不会不一定要在传入的数据相同`IEEDataStorage`对象，但返回的对象必须反映该属性的当前值。  
  
 EE 通常没有实现传入的数据对象。 但是，此方法返回的对象始终通过 EE，这样就 EE 实现实现`IEEDataStorage`上任何类所需的接口。  
  
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)方法创建一个基于传入的数据对象的数据对象，但不会影响该属性的原始数据。  
  
## <a name="see-also"></a>另请参阅  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
