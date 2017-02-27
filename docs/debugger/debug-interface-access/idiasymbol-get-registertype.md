---
title: "IDiaSymbol::get_registerType | Microsoft Docs"
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
ms.assetid: f1c98ab0-8aef-4a07-a686-28b8a54418ef
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_registerType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索注册类型。  
  
## 语法  
  
```cpp  
HRESULT get_registerType(   
   DWORD* pRetVal);  
```  
  
#### 参数  
 `pRetVal`  
 \[in\]保存注册类型为 `DWORD` 的指针。  
  
## 返回值  
 如果成功，则返回 `S_OK`，否则返回 `S_FALSE` 或者错误值代码。  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)