---
title: "IDebugArrayObject::GetDimensions | Microsoft Docs"
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
  - "IDebugArrayObject::GetDimensions"
helpviewer_keywords: 
  - "IDebugArrayObject::GetDimensions 方法"
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取数组的维数。  
  
## 语法  
  
```cpp#  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```c#  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### 参数  
 `dwCount`  
 \[in\] 检索的维数。  
  
 `dwDimensions`  
 \[in, out\] 在每个维度的范围填充的数组。  `dwCount` 指定 `dwDimensions` 数组的最大大小。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 多维数组可以具有每个维度的不同的范围。  例如命名三维数组 `myarray[3][2][6]`，则此方法返回 3， 2 和 6 的 `dwDimensions` 参数按此顺序。  
  
## 请参阅  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)