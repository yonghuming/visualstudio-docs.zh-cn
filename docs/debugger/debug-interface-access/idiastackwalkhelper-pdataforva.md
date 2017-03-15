---
title: "IDiaStackWalkHelper::pdataForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::pdataByVA 方法"
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

返回 PDATA 数据块与虚拟地址。  
  
## 语法  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### 参数  
 `va`  
 \[in\] 指定数据的虚拟地址获取。  
  
 `cbData`  
 \[in\] 数据的大小在获取的字节。  
  
 `pcbData`  
 \[out\] 在字节返回获取数据的实际大小。  
  
 `pbData`  
 \[in, out\] 用请求的数据填充的缓冲区。  不能为 `NULL`。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ; 如果没有为指定的地址， PDATA 返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 备注  
 PDATA \(名为 “.pdata”部分\) 编译包含有关异常处理的信息功能。  
  
 调用方知道数据量将返回，因此调用方不需要请求数数据可用。  因此，因此，如果 `pbData` 参数是 `NULL`，返回错误此方法的实现是可以接受的。  
  
## 请参阅  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)