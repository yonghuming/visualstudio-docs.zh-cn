---
title: "IDiaEnumInjectedSources::Item | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::Item 方法"
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumInjectedSources::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

通过索引检索插入的源。  
  
## 语法  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### 参数  
 Index — 索引  
 \[in\] 要检索的 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) 对象的索引。  索引是该范围 `count`0 到 \-1，其中 `count` 用 [IDiaEnumInjectedSources::get\_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) 方法返回。  
  
 injectedSource  
 \[out\] 返回表示已插入的源的 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)