---
title: "IDiaStackWalkHelper::imageForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper::imageForVA 方法"
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaStackWalkHelper::imageForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

返回一个可执行图像的开始对在可执行文件的内存空间提供的虚拟地址是内存的。  
  
## 语法  
  
```cpp#  
HRESULT imageForVA(  
   ULONGLONG  vaContext,  
   ULONGLONG *pvaImageStart  
);  
```  
  
#### 参数  
 `vaContext`  
 \[in\] 在可执行文件的空间在某处的虚拟地址。  
  
 `pvaImageStart`  
 \[out\] 返回可执行的图像的起始虚拟地址。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)