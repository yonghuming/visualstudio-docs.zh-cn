---
title: "IDiaDataSource::openSession | Microsoft Docs"
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
  - "IDiaDataSource::openSession 方法"
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

开始查询的符号一个会话。  
  
## 语法  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### 参数  
 ppSession  
 \[out\] 返回表示公开会话的 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  下表显示可能返回此方法的值。  
  
|值|说明|  
|-------|--------|  
|E\_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) 对象之前未初始化符号的源。|  
|E\_INVALIDARG|无效 `ppSession` 参数。|  
|E\_OUTOFMEMORY|启动会话中没有足够的内存。|  
  
## 备注  
 此方法打开数据源的一 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 对象。  
  
 `IDiaSession` 对象实现查询到数据源中。  会话管理每个地址空间设置调试符号。  如果数据源符号描述的 .exe 或 .dll 文件是一个多地址范围 \(例如，在中，因为多个进程将其加载\)，则应使用每个地址范围的一个会话。  
  
## 示例  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## 请参阅  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [概述](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [查询 .Pdb 文件](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)