---
title: "IDiaEnumDebugStreamData::Next | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Next 方法"
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索指定的记录数量。该枚举序列的。  
  
## 语法  
  
```cpp#  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### 参数  
 凯尔特人  
 \[in\] 要检索的记录数。  
  
 cbData  
 \[in\] 数据缓冲区的大小，以字节为单位\)。  
  
 pcbData  
 \[out\] 返回的字节数。  如果 `data` 为空，则 `pcbData` 包含总字节数数据可用于所有请求的记录。  
  
 数据 \[\]  
 \[out\] 将用调试流记录数据的缓冲区。  
  
 pceltFetched  
 \[in, out\] 返回的记录数。 `data`的。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果没有更多的记录，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 请参阅  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)