---
title: "IDiaStackWalkHelper::readMemory | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::readMemory 方法"
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

读取数据时阻止可执行图像的内存中。  
  
## 语法  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### 参数  
 `type`  
 \[in\] 从指定的内存的类型 [MemoryTypeEnum 枚举](../../debugger/debug-interface-access/memorytypeenum.md) 枚举的值读取。  
  
 VA  
 \[in\] 在开始的图像的虚拟地址读取。  
  
 `cbData`  
 \[in\] 数据缓冲区的大小 \(以字节为单位\)。  
  
 `pcbData`  
 \[out\] 返回实际读取的字节数。  如果 `pbData` 是 `NULL`，则这是总字节数可用的数据。  
  
 `pbData`  
 \[in, out\] 在读取的内存填充的缓冲区。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum 枚举](../../debugger/debug-interface-access/memorytypeenum.md)