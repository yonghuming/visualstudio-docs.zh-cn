---
title: "IDebugObject2::IsEncOutdated | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsEncOutdated"
helpviewer_keywords: 
  - "IDebugObject2::IsEncOutdated 方法"
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法确定是否编辑并继续此对象的状态或父容器已过时。  自定义表达式计算器不执行此方法并不总是返回 `E_NOTIMPL`。  
  
## 语法  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```c#  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### 参数  
 `pfEncOutdated`  
 \[out\] 非零 \(`TRUE`\)，则 " 编辑并继续 " 状态已过时，零 \(0\)`FALSE`\)，则不是。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
> [!NOTE]
>  自定义表达式计算器应始终返回 `E_NOTIMPL`。  
  
## 请参阅  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)