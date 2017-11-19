---
title: "IDebugObject2::GetBackingFieldForProperty |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords: IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2637ddf5d50953367de66cd2ca63d7774dbc3213
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
获取的字段或变量 （如果有），可能支持此对象表示的属性。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppObject`  
 [out][IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)描述支持字段的对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)对象表示托管的代码的类属性，即使用 get 方法和/或 set 访问器。 此类属性通常需要一个变量来包含操作的属性的值。 此变量被称为支持字段。 如果没有该对象不支持字段，则请确保将返回 null 值： 某些调用方可能注意不到返回的值，但将改为查看如果中返回了 null 值`ppObject`。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)