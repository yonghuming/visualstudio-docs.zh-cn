---
title: "IDiaEnumFrameData::Skip | Microsoft Docs"
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
  - "IDiaEnumFrameData::Skip 方法"
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumFrameData::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

跳过框架元素指定数目的枚举序列的。  
  
## 语法  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### 参数  
 凯尔特人  
 \[in\] 框架元素数。跳过的枚举序列的。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，因此，如果不再有要跳过，的非记录返回 `S_FALSE` 。  
  
## 请参阅  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)