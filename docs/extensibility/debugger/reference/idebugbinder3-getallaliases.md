---
title: "IDebugBinder3::GetAllAliases | Microsoft Docs"
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
  - "IDebugBinder3::GetAllAliases"
helpviewer_keywords: 
  - "IDebugBinder3::GetAllAliases 方法"
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法从程序检索别名列表。  
  
## 语法  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```c#  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### 参数  
 `uRequest`  
 \[in\] 返回的别名的最大数目 \(指定数组的长度传递给 `ppAliases`\)。  
  
 `ppAliases`  
 \[in, out\] 填充的数组使用别名 \(如果是空值，并 `uRequest` 为 0，可由返回的计数别名将由 `puFetched`返回\)。  
  
 `puFetched`  
 \[out\] 返回获得的别名的数目。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)