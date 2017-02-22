---
title: "IDebugObject::GetValue | Microsoft Docs"
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
  - "IDebugObject::GetValue"
helpviewer_keywords: 
  - "IDebugObject::GetValue 方法"
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::GetValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取对象的值作为字节顺序一系列更改。  
  
## 语法  
  
```cpp#  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```c#  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### 参数  
 `pValue`  
 \[in, out\] 用表示对象的值字节顺序的系列填充的数组。  
  
 `nSize`  
 \[in\] 获取的最大字节数。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 获取的值字节的总数可通过调用 [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) 方法获取。  
  
## 请参阅  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)