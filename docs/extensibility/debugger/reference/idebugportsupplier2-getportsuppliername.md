---
title: "IDebugPortSupplier2::GetPortSupplierName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::GetPortSupplierName"
helpviewer_keywords: 
  - "IDebugPortSupplier2::GetPortSupplierName"
ms.assetid: e4c368ab-640d-4b5b-9f74-810dc9364d8f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortSupplier2::GetPortSupplierName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取端口提供程序名称。  
  
## 语法  
  
```cpp#  
HRESULT GetPortSupplierName(   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetPortSupplierName(   
   out string pbstrName  
);  
```  
  
#### 参数  
 `pbstrName`  
 \[out\] 返回端口提供程序的名称。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)