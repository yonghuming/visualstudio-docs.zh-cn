---
title: "IEEDataStorage::GetData |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: f9642911606d9bbd72382fa1209484cded9bdf74
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
检索此对象中指定的字节数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dataSize`  
 [in]要检索的字节数 (`data`数组必须包含至少此数目的字节)。  
  
 `sizeGotten`  
 [out]返回实际检索的字节的数。  
  
 `data`  
 [在中，out]若要使用请求的数据填充的数组。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 建议的使用此方法是为本地数组时，检索数据的所有字节，因为没有方法跳过在检索过程中的字节。 在此情况下，参数`dataSize`应当值返回[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)方法。  
  
## <a name="see-also"></a>另请参阅  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)