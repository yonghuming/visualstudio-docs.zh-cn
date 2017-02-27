---
title: "IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive"
  - "GetTypeFromPrimitive"
ms.assetid: d7f51e2a-1b72-489c-b7b6-4af7b7e4d663
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索给定其基元类型的类型。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetTypeFromPrimitive(  
   DWORD         dwCorElementType,  
   IDebugField** ppType  
);  
```  
  
```c#  
int GetTypeFromPrimitive(  
   uint            dwCorElementType,  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwCorElementType`  
 [in]从值 [CorElementType 枚举](CorElementType%20Enumeration.xml) 表示基元类型。  
  
 `ppType`  
 [out]返回 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 表示的类型。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回 `S_OK`; 否则为返回错误代码。  
  
## <a name="see-also"></a>请参阅  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)