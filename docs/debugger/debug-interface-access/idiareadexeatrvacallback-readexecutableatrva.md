---
title: "IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs"
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
  - "IDiaReadExeAtRVACallback::ReadExecutableAtRVA 方法"
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

读取开始在从可执行文件中指定的相对虚拟地址的指定的 \(RVA\)字节数。  
  
## 语法  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### 参数  
 `relativeVirtualAddress`  
 \[in\] 在启动的可执行文件的类型读取。  
  
 `cbData`  
 \[in\] 读取的字节数。  
  
 `pcbData`  
 \[out\] 返回读取的字节数。  
  
 `data[]`  
 \[in, out\] 用字节填充的数组从文件读取。  
  
## 备注  
 使用相对虚拟地址，此方法由调用 DIA 支持代码从可执行文件加载数据字节。  此方法调用支持 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法。  
  
## 请参阅  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)