---
title: "IEEVisualizerDataProvider::GetNewObjectForVisualizer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider::GetNewObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::GetNewObjectForVisualizer 方法"
ms.assetid: a898d549-4898-4fde-aad1-e8bb89129652
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEEVisualizerDataProvider::GetNewObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法获取可视化工具的新对象。  该方法总是创建从现有对象的新对象。  
  
## 语法  
  
```cpp  
HRESULT GetNewObjectForVisualizer(  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int GetNewObjectForVisualizer(  
   out IDebugObject ppObject  
);  
```  
  
#### 参数  
 `ppObject`  
 \[out\] 新的对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 它 表示当前的`This method` 计算对象并返回结果作为新对象。  现有对象作为计算得到更新。  
  
## 请参阅  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)