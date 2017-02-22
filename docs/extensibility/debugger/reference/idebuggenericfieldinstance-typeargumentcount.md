---
title: "IDebugGenericFieldInstance::TypeArgumentCount | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TypeArgumentCount"
  - "IDebugGenericFieldInstance::TypeArgumentCount"
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugGenericFieldInstance::TypeArgumentCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回此实例的参数自变量类型的数目。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT TypeArgumentCount(  
   ULONG32* pcArgs  
);  
```  
  
```c#  
int TypeArgumentCount(  
   ref uint pcArgs  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pcArgs`  
 [在中，out]此实例的类型参数自变量数量。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回 `S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 例如，如果列表 \< int>, ，此方法返回 1，并且，如果列表 \< int、 float2 > 此方法返回 2。 如果不有任何类型参数，此方法将返回 0。  
  
## <a name="see-also"></a>请参阅  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)