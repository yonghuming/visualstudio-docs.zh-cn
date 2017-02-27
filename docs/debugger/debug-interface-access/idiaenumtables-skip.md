---
title: "IDiaEnumTables::Skip | Microsoft Docs"
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
  - "IDiaEnumTables::Skip 方法"
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumTables::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

跳过表指定数目的枚举序列的。  
  
## 语法  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### 参数  
 `celt`  
 \[in\] 表数在跳过的枚举序列的。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，因此，如果不再有要跳过，的非表返回 `S_FALSE` 。  
  
## 请参阅  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)