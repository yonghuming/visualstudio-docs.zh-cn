---
title: "IDebugArrayObject::GetElements |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetElements
helpviewer_keywords: IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60b267964b58dff8365ee6f769ee6b81f1bfb066
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
获取枚举数的数组的所有元素。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppEnum`  
 [out]返回[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)对象，它允许枚举的所有元素。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 作为替代方法，使用[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)和[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)方法循环访问元素。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)