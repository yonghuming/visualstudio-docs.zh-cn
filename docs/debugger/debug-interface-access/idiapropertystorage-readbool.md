---
title: "IDiaPropertyStorage::ReadBOOL | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadBOOL"
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

阅读设置的属性的 `BOOL` 值。  
  
## 语法  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### 参数  
 `id`  
 \[in\] 要读取的属性的标识符 \(`PROPID` 在 WTypes.h 中定义为 `ULONG`\)。  
  
 `pValue`  
 \[out\] 返回属性值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  ，如果属性不是类型 `BOOL`，返回 `E_INVALIDARG` 。  
  
## 备注  
 对于一致的结果，请解释 `BOOL` 值，以便非零值是 `TRUE` ，而零是 `FALSE`。  
  
## 请参阅  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)