---
title: "IDiaLoadCallback2 | Microsoft Docs"
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
  - "IDiaLoadCallback2 接口"
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaLoadCallback2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

接收查找程序的 DIA 符号的回调，允许限制施加位于过程。  
  
## 语法  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## 方法按 Vtable 顺序  
 除了在 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) 接口的方法之外，此接口公开下列方法:  
  
|方法|说明|  
|--------|--------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|确定是否位于原始上的 .pdb 文件调试目录。|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../Topic/IDiaLoadCallback2::RestrictReferencePathAccess.md)|确定查找 .pdb 文件在找到 .exe 文件的路径允许的。|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|确定查找是否调试信息从 .dbg 文件授予权限。|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|确定搜索 .pdb 文件在系统根目录允许的。|  
  
## 备注  
 客户端应用程序实现此接口并提供对它在对 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法。  确保在执行任何 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) 接口的方法。  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia80.dll  
  
## 请参阅  
 [接口（调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)