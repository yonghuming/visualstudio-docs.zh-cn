---
title: "IDiaSymbol::get_dataBytes | Microsoft Docs"
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
  - "IDiaSymbol::get_dataBytes 方法"
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_dataBytes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索 OEM 符号的数据字节。  
  
## 语法  
  
```cpp#  
HRESULT get_dataBytes (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### 参数  
 `cbData`  
 \[in\] 存储数据的缓冲区的大小。  
  
 `pcbData`  
 \[out\] 返回编写的字节数，或者，如果 `data` 参数是 `NULL`，返回可用的字节数。  
  
 `data[]`  
 \[\] 字节，用数据填充的缓冲区。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` 或错误代码。  
  
> [!NOTE]
>  `S_FALSE` 的返回值表示该属性用于符号不可用。  
  
## 要求  
  
|要求|说明|  
|--------|--------|  
|标题:|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)