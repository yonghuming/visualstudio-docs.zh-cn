---
title: "IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaPropertyStorage::ReadULONGLONG"
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

阅读设置的属性的 `ULONGLONG` 值。  
  
## 语法  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### 参数  
 `id`  
 \[in\] 要读取的属性的标识符 \(`PROPID` 在 WTypes.h 中定义为 `ULONG`\)。  
  
 `pValue`  
 \[out\] 返回属性值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  ，如果属性不是类型 `ULONGLONG`，返回 `E_INVALIDARG` 。  
  
## 备注  
 `ULONGLONG` 是 windows 定义为 64 位无符号整数。  
  
## 请参阅  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)