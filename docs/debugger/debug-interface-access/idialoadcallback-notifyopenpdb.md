---
title: "IDiaLoadCallback::NotifyOpenPDB | Microsoft Docs"
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
  - "IDiaLoadCallback::NotifyOpenPDB 方法"
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::NotifyOpenPDB
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

调用，在打开候选 .pdb 文件。  
  
## 语法  
  
```cpp#  
HRESULT NotifyOpenPDB (   
   LPCOLESTR pdbPath,  
   HRESULT   resultCode  
);  
```  
  
#### 参数  
 `pdbPath`  
 \[in\] .pdb 文件的完整路径。  
  
 `resultCode`  
 \[in\] 代码指示负载的成功 \(`S_OK`\) 或失败应用于此文件。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  返回代码通常被忽略。  
  
## 请参阅  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)