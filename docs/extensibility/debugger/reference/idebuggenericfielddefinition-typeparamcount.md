---
title: "IDebugGenericFieldDefinition::TypeParamCount | Microsoft Docs"
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
  - "TypeParamCount"
  - "IDebugGenericFieldDefinition::TypeParamCount"
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugGenericFieldDefinition::TypeParamCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索与泛型字段关联的类型参数的数目。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT TypeParamCount(  
   ULONG32* pcParams  
);  
```  
  
```c#  
int TypeParamCount(  
   ref uint pcParams  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pcParams`  
 [在中，out]类型参数的数目。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回 `S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 如果列表 \< T>, ，此方法返回 1，并且，如果列表 \< T1、 T2 >，此方法返回 2。 如果没有类型参数，此方法将返回 0。  
  
## <a name="see-also"></a>请参阅  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)