---
title: "IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider::SetObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::SetObjectForVisualizer 方法"
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法更改可视化表示的对象。  
  
## 语法  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```c#  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### 参数  
 `pNewObject`  
 \[in\] 设置的对象。  
  
 `error`  
 \[out\] 如果具有对象的错误，该字符串包含错误消息。  
  
 `pException`  
 \[out\] 如果出现错误，此对象包含异常信息。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 应确定错误信息如何实现返回。  但是，可以将某些调用方只查找查看异常对象是否返回已知有错误，因此，此方法应始终返回异常对象，则出现错误。  错误字符串，如果调用方希望利用它，还应提供。  
  
## 请参阅  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)