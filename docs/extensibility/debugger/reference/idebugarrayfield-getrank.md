---
title: "IDebugArrayField::GetRank | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetRank"
helpviewer_keywords: 
  - "IDebugArrayField::GetRank 方法"
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取数组维度的级别或数量。  
  
## 语法  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```c#  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### 参数  
 `pdwRank`  
 \[out\] 返回一个级别。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 数组的秩对应维度数。  因此在 C\+\+ 和 c\# 中，多维数组实际上是数组，并可以考虑一维数组 \(和 `GetRank` 方法始终返回 1\)。  在 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]，另一方面，多维数组不同，并且这类数组级别反映维 \(和 `GetRank` 方法的数字始终返回维度数\)。  
  
## 请参阅  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)