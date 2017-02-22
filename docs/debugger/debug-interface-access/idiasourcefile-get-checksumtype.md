---
title: "IDiaSourceFile::get_checksumType | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksumType 方法"
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索检查和类型。  
  
## 语法  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] 返回检查和类型。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 检查和类型是可以映射到检查和算法的值。  例如，标准 PDB 文件格式通常可具有下列值之一:  
  
|检查和类型|CryptoAPI 标签|说明|  
|-----------|------------------|--------|  
|0|\<none\>|不检查和存在。|  
|1|`CALG_MD5`|检查和生成与 MD5 哈希算法。|  
|2|`CALG_SHA1`|检查和生成使用 SHA1 哈希算法。|  
  
 `CryptoAPI` 标签是从 `ALG_ID` 枚举。  有关哈希算法的更多信息，请参见 Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)]的 `CryptoAPI` 部分。  
  
 若要获取源文件的实际检查和字节，请调用 [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) 方法。  
  
## 请参阅  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)