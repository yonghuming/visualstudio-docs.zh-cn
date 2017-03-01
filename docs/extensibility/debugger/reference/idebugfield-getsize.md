---
title: "IDebugField::GetSize |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
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
ms.openlocfilehash: ef74d7e7ff50691aace25108facf60ef17d6c8cf
ms.lasthandoff: 02/22/2017

---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
此方法获取字段中，以字节为单位的大小。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetSize(   
   DWORD* pdwSize  
);  
```  
  
```c#  
int GetSize(  
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdwSize`  
 [out]返回的大小。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 所有字段都具有一种类型和所有类型都有一个大小。 例如，具有一种类型的字节的域具有 1 个字节的大小。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
