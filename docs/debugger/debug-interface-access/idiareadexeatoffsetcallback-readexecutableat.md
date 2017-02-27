---
title: "IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs"
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
  - "IDiaReadExeAtOffsetCallback::ReadExecutableAt 方法"
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

读取开始在从可执行文件中指定的偏移量指定的字节数。  
  
## 语法  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### 参数  
 fileOffset  
 \[in\] 在启动的可执行文件的偏移量读取。  
  
 cbData  
 \[in\] 读取的字节数。  
  
 pcbData  
 \[out\] 返回读取的字节数。  
  
 数据 \[\]  
 \[in, out\] 用字节填充的数组从文件读取。  
  
## 备注  
 使用绝对文件偏移量，此方法由调用 DIA 支持代码从可执行文件加载数据字节。  此方法调用支持 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法。  
  
## 请参阅  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)