---
title: "IDiaSymbol::get_isSdl | Microsoft Docs"
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
ms.assetid: 6aa0e116-da75-4643-a4d7-d8e142231e21
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isSdl
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定模块是否使用\/SDL选项编译。  
  
## 语法  
  
```cpp  
HRESULT get_isSdl(  
   BOOL *pRetVal);  
```  
  
#### 参数  
 `pRetVal`  
 \[in\]指定要 `BOOL` 的指针模块是否使用\/SDL选项编译。  
  
## 返回值  
 如果成功，则返回 `S_OK`，否则返回 `S_FALSE` 或者错误值代码。  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)