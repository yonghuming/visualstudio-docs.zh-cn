---
title: "IPropertyProxyEESide::CreateReplacementObject |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords: IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0f0202f017004e69f356b31299f0ed28b55348aa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
创建数据对象的副本特定于表达式计算器 (EE)。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dataIn`  
 [in][IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)存放要复制的数据对象。  
  
 `dataOut`  
 [out]返回一个新`IEEDataStorage`对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 此方法有[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)表示的字节数组对象。 通常是由 EE 不实现此传入的数据对象。 但是，此方法返回的对象始终由 EE，这样就 EE 实现`IEEDataStorage`上任何类所需的接口。  
  
 请注意，数据提供通过传入`IEEDataStorage`对象必须是相同的数据中的传出`IEEDataStorage`对象。  
  
## <a name="see-also"></a>另请参阅  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)