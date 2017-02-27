---
title: "IDiaStackWalkHelper::put_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::put_registerValue 方法"
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

设置寄存器值。  
  
## 语法  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### 参数  
 `index`  
 \[in\] 从指定注册的 [CV\_HREG\_e 枚举](../../debugger/debug-interface-access/cv-hreg-e.md) 枚举的值写入。  
  
 `NewVal`  
 \[in\] 新的寄存器值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 尽管该值的范围，实施者应只存储哪些注册通常保留。  例如，一个 8 位寄存器会保存给定值的最低的 8 位。  
  
## 请参阅  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV\_HREG\_e 枚举](../../debugger/debug-interface-access/cv-hreg-e.md)