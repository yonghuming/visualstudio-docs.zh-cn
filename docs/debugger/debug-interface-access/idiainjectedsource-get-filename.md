---
title: "IDiaInjectedSource::get_filename | Microsoft Docs"
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
  - "IDiaInjectedSource::get_filename 方法"
ms.assetid: 20f4fc68-335a-4971-b3a6-76501f0e8b19
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaInjectedSource::get_filename
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索数据源的文件名。  
  
## 语法  
  
```cpp#  
HRESULT get_filename (   
   BSTR* pRetVal  
);  
```  
  
#### 参数  
 pRetVal  
 \[out\] 返回数据源的文件名。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果此属性不受支持，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 请参阅  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)