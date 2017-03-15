---
title: "IDiaPropertyStorage::ReadDWORD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaPropertyStorage::ReadDWORD"
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaPropertyStorage::ReadDWORD
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

阅读设置的属性的 `DWORD` 值。  
  
## 语法  
  
```cpp#  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### 参数  
 `id`  
 \[in\] 要读取的属性的标识符 \(`PROPID` 在 WTypes.h 中定义为 `ULONG`\)。  
  
 `pValue`  
 \[out\] 返回属性值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  ，如果属性不是类型 `DWORD`，返回 `E_INVALIDARG` 。  
  
## 备注  
 `DWORD` 是 windows 定义为 32 位无符号整数。  
  
## 请参阅  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)