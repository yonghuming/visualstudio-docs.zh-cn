---
title: "IDebugGenericFieldDefinition::GetFormalTypeParams | Microsoft Docs"
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
  - "GetFormalTypeParams"
  - "IDebugGenericFieldDefinition::GetFormalTypeParams"
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugGenericFieldDefinition::GetFormalTypeParams
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索给定的参数数目的类型参数。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```c#  
int GetFormalTypeParams(  
   uint                          cParams,  
   out IDebugGenericParamField[] ppParams,  
   ref uint                      pcParams  
);  
```  
  
#### <a name="parameters"></a>参数  
 `cParams`  
 [in]参数数目。  
  
 `ppParams`  
 [out]类型参数的数组。  
  
 `pcParams`  
 [在中，out]中的参数数目 `ppParams` 数组。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回 `S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 返回的类型参数按顺序从左到右。 例如，字典 \< K，V > 将返回 IDebugFormalGenericParameters {K，V}。  
  
## <a name="see-also"></a>请参阅  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)