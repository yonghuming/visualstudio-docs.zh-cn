---
title: "IDiaStackWalkHelper::get_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::get_registerValue 方法"
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaStackWalkHelper::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索注册的值。  
  
## 语法  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### 参数  
 `index`  
 \[in\] 从指定的 [CV\_HREG\_e 枚举](../../debugger/debug-interface-access/cv-hreg-e.md) 枚举的值注册捕获值。  
  
 `pRetVal`  
 \[out\] 返回注册的当前值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 尽管 `pRetVal` 参数的大小，实施者应只存储哪些注册通常保留。  例如，一个 8 位寄存器保存给定值的最低的 8 位。  该 8 位值展开为 64 位，当返回从此方法。  
  
## 请参阅  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV\_HREG\_e 枚举](../../debugger/debug-interface-access/cv-hreg-e.md)