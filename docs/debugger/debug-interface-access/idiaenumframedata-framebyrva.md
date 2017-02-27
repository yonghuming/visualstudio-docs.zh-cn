---
title: "IDiaEnumFrameData::frameByRVA | Microsoft Docs"
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
  - "IDiaEnumFrameData::frameByRVA 方法"
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumFrameData::frameByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

由相对虚拟地址返回帧 \(RVA\)。  
  
## 语法  
  
```cpp#  
HRESULT frameByRVA(   
   DWORD           relativeVirtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### 参数  
 relativeVirtualAddress  
 \[in\] 框架的类型相关。  
  
 框架  
 \[out\] 返回表示包含提供的地址帧的 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 对象。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果帧数据不与指定的地址，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 请参阅  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)