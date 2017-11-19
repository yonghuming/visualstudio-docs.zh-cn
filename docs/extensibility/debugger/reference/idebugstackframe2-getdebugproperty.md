---
title: "IDebugStackFrame2::GetDebugProperty |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame2::GetDebugProperty
helpviewer_keywords: IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1340313a66a3c58759f1cd91bc967a3d95ac93ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
获取一个堆栈帧的属性的说明。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppDebugProp  
);  
```  
  
```csharp  
int GetDebugProperty (   
   out IDebugProperty2 ppDebugProp  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppDebugProp`  
 [out]返回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介绍此堆栈帧的属性的对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 调用[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)与相应的筛选器的方法可以检索的本地变量、 方法参数、 寄存器以及与堆栈帧关联"this"指针。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)