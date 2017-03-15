---
title: "IDiaPropertyStorage::ReadBSTR | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadBSTR"
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaPropertyStorage::ReadBSTR
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

阅读设置的属性的 `BSTR` 值。  
  
## 语法  
  
```cpp#  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### 参数  
 `id`  
 \[in\] 要读取的属性的标识符 \(`PROPID` 在 WTypes.h 中定义为 `ULONG`\)。  
  
 `pValue`  
 \[out\] 返回属性值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  ，如果属性不是类型 `BSTR`，返回 `E_INVALIDARG` 。  
  
## 备注  
 `BSTR` 是 windows 定义为零结尾的宽字符字符串。  
  
## 请参阅  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)