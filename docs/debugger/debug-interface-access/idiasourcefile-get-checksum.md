---
title: "IDiaSourceFile::get_checksum | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksum 方法"
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索检查和字节。  
  
## 语法  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### 参数  
 `cbData`  
 \[in\] 数据缓冲区的大小，以字节为单位\)。  
  
 `pcbData`  
 \[out\] 返回检查和字节的数目。  此参数不能为 `NULL`。  
  
 `data`  
 \[in, out\] 填充检查和字节的缓冲区。  如果此参数是 `NULL`，则 `pcbData` 返回所需的字节数。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 若要确定的校验和算法的类型用于生成检查和字节，请调用 [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) 方法。  
  
 检查和从源文件的图像时生成的，因此在源文件中的更改将反映在检查和字节的更改。  如果校验和字节不匹配从文件中加载的图像生成的校验和，则应考虑文件已损坏或篡改。  
  
 典型的校验和的大小不大于 32 个字节，但不会假定是检查和的最大大小。  设置 `data` 参数传递给 `NULL` 访问要求的字节数检索校验和。  然后将适当大小的缓冲区并更调用此方法用新的缓冲区。  
  
## 请参阅  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)