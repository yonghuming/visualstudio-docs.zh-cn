---
title: "IDiaEnumStackFrames::Next | Microsoft Docs"
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
  - "IDiaEnumStackFrames::Next 方法"
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumStackFrames::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

枚举序列以检索堆栈帧指定数量的元素。  
  
## 语法  
  
```cpp#  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### 参数  
 凯尔特人  
 \[in\] stackframe 元素数在枚举数将检索。  
  
 rgelt  
 \[out\] 将通过请求的 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) 填充的对象的数组。  
  
 pceltFetched  
 \[out\] 返回由枚举中获取的枚举数的堆栈帧元素的数目。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果没有更多的堆栈帧，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 请参阅  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)