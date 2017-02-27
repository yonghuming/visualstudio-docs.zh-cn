---
title: "IDiaSymbol::get_uavSlot | Microsoft Docs"
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
ms.assetid: a70648f2-3b25-439f-8099-239ac602515a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_uavSlot
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索uav槽。  
  
## 语法  
  
```cpp  
HRESULT get_uavSlot(   
   DWORD* pRetVal);  
```  
  
#### 参数  
 `pRetVal`  
 \[in\]保存uav槽到 `DWORD` 的指针。  
  
## 返回值  
 如果成功，则返回 `S_OK`，否则返回 `S_FALSE` 或者错误值代码。  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)