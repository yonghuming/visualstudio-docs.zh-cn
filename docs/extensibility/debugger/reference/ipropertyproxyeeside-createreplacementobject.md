---
title: "IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
helpviewer_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

创建数据对象特定的副本将表达式计算器 \(EE\)。  
  
## 语法  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### 参数  
 `dataIn`  
 \[in\] 存储数据的 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 对象的文件夹。  
  
 `dataOut`  
 \[out\] 返回一个新的 `IEEDataStorage` 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 产生此方法表示字节的一 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 对象。  此传入数据对象不受 EE 通常实现。  但是，此方法返回的对象由 EE 总是实现，允许 EE `IEEDataStorage` 实现接口的任何类希望。  
  
 请注意传入的 `IEEDataStorage` 对象提供的数据必须位于传出 `IEEDataStorage` 对象的相同数据。  
  
## 请参阅  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)