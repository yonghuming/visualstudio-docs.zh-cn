---
title: "IDebugReference2::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::GetParent"
helpviewer_keywords: 
  - "IDebugReference2::GetParent"
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::GetParent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取父引用。  保留供将来使用。  
  
## 语法  
  
```cpp#  
HRESULT GetParent (   
   IDebugReference2** ppParent  
);  
```  
  
```c#  
int GetParent (   
   out IDebugReference2 ppParent  
);  
```  
  
#### 参数  
 `ppParent`  
 \[out\] 返回表示此属性的父级的 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 对象。  
  
## 返回值  
 始终返回 `E_NOTIMPL`。  
  
## 请参阅  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)