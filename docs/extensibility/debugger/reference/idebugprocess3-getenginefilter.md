---
title: "IDebugProcess3::GetEngineFilter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetEngineFilter"
  - "IDebugProcess3::GetEngineFilter"
ms.assetid: ccb7ecb0-f189-4e80-b5b2-221a095e01f5
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProcess3::GetEngineFilter
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索数组可用的唯一标识符调试引擎。  
  
## 语法  
  
```cpp#  
HRESULT GetEngineFilter(  
   GUID_ARRAY *pEngineArray  
);  
```  
  
```c#  
public int GetEngineFilter(  
   out GUID_ARRAY[] pEngineArray  
);  
```  
  
#### 参数  
 `pEngineArray`  
 \[out\] 对包含唯一标识符调试引擎的结构。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GUID\_ARRAY](../../../extensibility/debugger/reference/guid-array.md)