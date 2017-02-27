---
title: "IDebugArrayObject::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetCount"
helpviewer_keywords: 
  - "IDebugArrayObject::GetCount 方法"
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugArrayObject::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取计数在数组的元素。  
  
## 语法  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### 参数  
 `pdwElements`  
 \[out\] 返回计数。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 此方法来查看所有数组对象元素作为一维数组，因此，即使数组对象是多维的。  例如将该数组 `myarray[3][2][6]`，则此方法返回 36。 `pdwElements` 参数。  使用 [GetElement](../Topic/IDebugArrayObject::GetElement.md) 方法检索各个元素一次一条记录。  
  
## 请参阅  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)