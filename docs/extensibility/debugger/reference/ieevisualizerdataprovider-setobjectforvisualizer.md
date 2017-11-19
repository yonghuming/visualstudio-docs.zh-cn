---
title: "IEEVisualizerDataProvider::SetObjectForVisualizer |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords: IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76a901401e854611cc987ac5c0cf8eeabb8dfd53
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
此方法可更改可视化工具表示的对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pNewObject`  
 [in]要设置的对象。  
  
 `error`  
 [out]如果没有设置该对象时出现错误，此字符串将包含错误消息。  
  
 `pException`  
 [out]如果没有错误，此对象包含的异常信息。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 它是取决于实施者，以确定如何返回错误信息。 但是，很可能某些调用方可能唯一查看，请参阅是否返回了异常对象以知道有错误，因此如果出错，此方法始终应返回异常对象。 在调用方想要对进行的情况下，还应提供的错误字符串使用它。  
  
## <a name="see-also"></a>另请参阅  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)