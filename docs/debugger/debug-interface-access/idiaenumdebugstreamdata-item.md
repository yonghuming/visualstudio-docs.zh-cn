---
title: "IDiaEnumDebugStreamData::Item | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumDebugStreamData::Item 方法"
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreamData::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索具有指定的记录。  
  
## 语法  
  
```cpp#  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### 参数  
 Index — 索引  
 \[in\] 要检索的记录的索引。  索引范围在 0 到 `count`\-1，其中 `count` 由 [IDiaEnumDebugStreamData::get\_Count](../Topic/IDiaEnumDebugStreamData::get_Count.md)返回。  
  
 cbData  
 \[in\] 数据缓冲区的大小，以字节为单位\)。  
  
 pcbData  
 \[out\] 返回的字节数。  如果 `data` 是 `NULL`，则 `pcbData` 包含总字节数数据可用于在指定的记录。  
  
 数据 \[\]  
 \[out\] 使用调试流记录数据填充的缓冲区。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  返回 void 参数的 `E_INVALIDARG` ，并且，如果 `index` 参数是在区域之外。  
  
## 请参阅  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreamData::get\_Count](../Topic/IDiaEnumDebugStreamData::get_Count.md)   
 [IDiaEnumDebugStreamData::Skip](../Topic/IDiaEnumDebugStreamData::Skip.md)