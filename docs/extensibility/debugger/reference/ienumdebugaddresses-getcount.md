---
title: "IEnumDebugAddresses::GetCount |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugAddresses::GetCount
helpviewer_keywords: IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e03a8c35a2e0bae6748bfe9737e8e21923390762
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
此方法在枚举中返回元素的数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pcelt`  
 [out]枚举中返回元素的数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 此方法不是通常的 COM 枚举接口指定下, 一步、 克隆、 跳过和重置需要实现的一部分。  
  
## <a name="see-also"></a>另请参阅  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)