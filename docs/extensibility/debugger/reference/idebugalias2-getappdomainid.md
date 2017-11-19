---
title: "IDebugAlias2::GetAppDomainId |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b4d5dacd7a614981971c691d3c06c436eaf55008
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
检索应用程序域的标识符。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```csharp  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pappDomainId`  
 [out]返回应用程序域标识符。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 创建应用程序域标识符更改时重新启动应用程序和新的应用程序域。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)