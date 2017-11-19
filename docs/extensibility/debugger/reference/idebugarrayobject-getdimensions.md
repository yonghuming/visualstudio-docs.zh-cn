---
title: "IDebugArrayObject::GetDimensions |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetDimensions
helpviewer_keywords: IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d516032e458bcc0f85c73c75a9147ff53fc0fff2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
获取数组的维数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwCount`  
 [in]要检索的维度数。  
  
 `dwDimensions`  
 [在中，out]使用每个维度的大小填充数组。 `dwCount`指定的最大大小`dwDimensions`数组。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 多维数组可具有不同大小为每个维度。 例如，给定的三维数组`myarray[3][2][6]`，此方法将返回 3、 2 和 6 英寸`dwDimensions`按此顺序的参数。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)