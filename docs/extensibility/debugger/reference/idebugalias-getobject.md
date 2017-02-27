---
title: "IDebugAlias::GetObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::GetObject"
helpviewer_keywords: 
  - "IDebugAlias::GetObject 方法"
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugAlias::GetObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取对象此别名。  
  
## 语法  
  
```cpp  
HRESULT GetObject(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetObject(  
   Out IDebugObject2 ppObject  
)  
```  
  
#### 参数  
 `ppObject`  
 \[out\] 此别名表示的 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) 。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 请参阅  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)