---
title: "IDebugArrayObject::GetRank |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetRank
helpviewer_keywords: IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3ef04279c4a9e34313c7d449714cb0a519d5652
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
获取数组，即维度数的秩。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdwRank`  
 [out]返回的排名。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 使用[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)方法来检索每个维度的数组对象的大小。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)