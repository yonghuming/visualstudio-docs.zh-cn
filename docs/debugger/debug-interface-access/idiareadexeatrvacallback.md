---
title: "IDiaReadExeAtRVACallback | Microsoft Docs"
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
  - "IDiaReadExeAtRVACallback 接口"
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaReadExeAtRVACallback
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

启用客户端应用程序提供可执行文件的字节为指定的相对虚拟地址。  
  
## 语法  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## 方法按 Vtable 顺序  
 下表显示 `IDiaReadExeAtRVACallback`方法。  
  
|方法|说明|  
|--------|--------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|读取开始在从可执行文件中指定的相对虚拟地址的指定的 \(RVA\)字节数。|  
  
## 备注  
 客户端应用程序实现此接口以便提供字节可执行文件使用相对虚拟地址到可执行文件。  若要使用绝对文件偏移量，请实现 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) 接口。  
  
## 调用方的说明  
 此方法由客户端应用程序执行并传递给 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法作为读取的文件的另一种方法。  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia80.dll  
  
## 请参阅  
 [接口（调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)