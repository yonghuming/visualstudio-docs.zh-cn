---
title: "IDiaDataSource::get_lastError | Microsoft Docs"
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
  - "IDiaDataSource::get_lastError 方法"
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索最后加载错误的文件名。  
  
## 语法  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### 参数  
 pRetVal  
 \[out\] 返回包含 .pdb 文件名与最后加载错误的字符串。  
  
## 返回值  
 返回加载操作导致的上一个错误代码。  ，如果 `pRetVal` 参数是 `NULL`，返回 `E_INVALIDARG` 。  
  
## 示例  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## 请参阅  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)