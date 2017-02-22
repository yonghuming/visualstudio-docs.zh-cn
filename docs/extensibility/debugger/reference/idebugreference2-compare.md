---
title: "IDebugReference2::Compare | Microsoft Docs"
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
  - "IDebugReference2::Compare"
helpviewer_keywords: 
  - "IDebugReference2::Compare"
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

比较对另一个。  保留供将来使用。  
  
## 语法  
  
```cpp#  
HRESULT Compare (   
   REFERENCE_COMPARE dwCompare,  
   IDebugReference2* pReference  
);  
```  
  
```c#  
int Compare (   
   enum_REFERENCE_COMPARE dwCompare,  
   IDebugReference2       pReference  
);  
```  
  
#### 参数  
 `dwCompare`  
 \[in\] 从指定比较操作，例如， equals 的 [REFERENCE\_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) 枚举的值，、小于或大于。  
  
 `pReference`  
 \[in\] 表示引用的 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 对象进行比较。  
  
## 返回值  
 始终返回 `E_NOTIMPL`。  
  
## 请参阅  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE\_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)