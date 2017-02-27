---
title: "IDiaEnumSourceFiles::Item | Microsoft Docs"
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
  - "IDiaEnumSourceFiles::Item 方法"
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSourceFiles::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

通过索引检索源文件。  
  
## 语法  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaSourceFile** sourceFile  
);  
```  
  
#### 参数  
 Index — 索引  
 \[in\] 要检索的 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 对象的索引。  索引范围在 0 到 `count`\-1，其中`count` 用 [IDiaEnumSourceFiles::get\_Count](../Topic/IDiaEnumSourceFiles::get_Count.md) 方法返回。  
  
 sourceFile  
 \[out\] 返回表示所需的源文件的 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)