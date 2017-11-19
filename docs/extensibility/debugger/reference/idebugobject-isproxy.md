---
title: "IDebugObject::IsProxy |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 40c1b54c8da094ed48685bd59789290f4206699a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
确定对象是否为透明的代理。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT IsProxy (  
   BOOL* pfIsProxy  
);  
```  
  
```csharp  
int IsProxy (  
   out bool pfIsProxy  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pfIsProxy`  
 [out]`TRUE`如果对象是透明的代理; 否则为`FALSE`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 此方法由实现默认 c + + 调试引擎。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)