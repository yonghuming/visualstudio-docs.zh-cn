---
title: "IDebugField::GetContainer | Microsoft Docs"
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
  - "IDebugField::GetContainer"
helpviewer_keywords: 
  - "IDebugField::GetContainer 方法"
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugField::GetContainer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法获取域的容器。  
  
## 语法  
  
```cpp#  
HRESULT GetContainer(   
   IDebugContainerField** ppContainerField  
);  
```  
  
```c#  
int GetContainer(  
   out IDebugContainerField ppContainerField  
);  
```  
  
#### 参数  
 `ppContainerField`  
 \[out\] 返回容器如由 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 接口。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 如果此字段没有容器，返回的 `ppContainerField` 将空值。  
  
## 请参阅  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)