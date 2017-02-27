---
title: "IDiaLineNumber::get_columnNumberEnd | Microsoft Docs"
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
  - "IDiaLineNumber::get_columnNumberEnd 方法"
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_columnNumberEnd
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索表达式或语句结束从一开始的源列数。  
  
## 语法  
  
```cpp#  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] 返回表达式或语句结束的列数。  如果该值为零，则列结尾信息不存在。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果此属性不受支持，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 备注  
 此方法返回的列值是一个字节的偏移量行中对位置在语句中最后一个字符之后在行。  
  
## 请参阅  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)