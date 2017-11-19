---
title: "IDebugEngine2::SetMetric |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2:::SetMetric
helpviewer_keywords: IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 125cedb79be629e6024e90afef16b34e57d94571
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
此方法设置的注册表值，称为某个度量值。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```csharp  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pszMetric`  
 [in]度量值的名称。  
  
 `varValue`  
 [in]指定度量值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 指标是用于更改调试引擎的行为或播发受支持的功能的注册表值。 此方法可以将其转发到相应的窗体的调用[SDK 以便进行调试的帮助器](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)函数， `SetMetric`。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [用于调试的 SDK 帮助程序](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)