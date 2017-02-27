---
title: "IDiaFrameData::get_allocatesBasePointer | Microsoft Docs"
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
  - "IDiaFrameData::get_allocatesBasePointer 方法"
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaFrameData::get_allocatesBasePointer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索指示的标志基本指针是否为在该地址范围的代码分配。  此方法已被否决。  
  
## 语法  
  
```cpp#  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] ，如果分配了，则返回 `TRUE` 基本指针;否则，返回 `FALSE`。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果此属性不受支持，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 备注  
 应由以前访问 FPO\_DATA 的代码才能使用此属性，或者，在 [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) 方法返回的程序字符串是 `NULL`时。  否则，程序字符串包含所需的所有信息计算前面的寄存器值。  
  
## 请参阅  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)