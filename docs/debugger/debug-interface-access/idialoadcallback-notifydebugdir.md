---
title: "IDiaLoadCallback::NotifyDebugDir | Microsoft Docs"
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
  - "IDiaLoadCallback::NotifyDebugDir 方法"
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

调用，在调试内容在 .exe 文件中找到。  
  
## 语法  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### 参数  
 `fExecutable`  
 \[in\] `TRUE` ，如果调试目录从可执行读取 \(而不是 .dbg 文件\)。  
  
 `cbData`  
 \[in\] 计数字节在调试目录的数据。  
  
 `data[]`  
 \[in\] 使用调试内容填充的数组。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  返回代码通常被忽略。  
  
## 备注  
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法调用该回调，当找到一个调试目录时，托管可执行文件时。  
  
 此方法在 .pdb 文件中移除对客户端的需要写入反向工程处理可执行文件和\/或调试文件支持调试信息除此之外找到。  具有此数据，客户端可以识别调试的类型信息提供的，它是否位于可执行文件或 .dbg 文件。  
  
 大多数客户端不需要此回调，因为 `IDiaDataSource::loadDataForExe` 方法透明地打开 .pdb 和 .dbg 文件，如果必要服务符号。  
  
## 请参阅  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)