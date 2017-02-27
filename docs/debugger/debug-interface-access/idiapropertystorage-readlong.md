---
title: "IDiaPropertyStorage::ReadLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadLONG"
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaPropertyStorage::ReadLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

阅读设置的属性的 `LONG` 值。  
  
## 语法  
  
```cpp#  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### 参数  
 `id`  
 \[in\] 要读取的属性的标识符 \(`PROPID` 在 WTypes.h 中定义为 `ULONG`\)。  
  
 `pValue`  
 \[out\] 返回属性值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  ，如果属性不是类型 `LONG`，返回 `E_INVALIDARG` 。  
  
## 备注  
 `LONG` 是 windows 定义的作为 32 位带符号整数。  
  
## 请参阅  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)