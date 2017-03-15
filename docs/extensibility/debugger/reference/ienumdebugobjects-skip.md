---
title: "IEnumDebugObjects::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects::Skip"
helpviewer_keywords: 
  - "IEnumDebugObjects::Skip 方法"
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumDebugObjects::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法跳过元素指定数目的。  
  
## 语法  
  
```cpp#  
HRESULT Skip(  
   [in] ULONG celt  
);  
```  
  
```c#  
int Skip(  
   [In] uint celt  
);  
```  
  
#### 参数  
 `celt`  
 \[in\] 跳过的元素数。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  返回 `S_FALSE` ，如果 `celt` 比其余元素的数量大于;否则，返回错误代码。  
  
## 备注  
 如果 `celt` 比剩余的元素数指定值，枚举设置为末尾，并 `S_FALSE` 返回。  
  
## 请参阅  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)