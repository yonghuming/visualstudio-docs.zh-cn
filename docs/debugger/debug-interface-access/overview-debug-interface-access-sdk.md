---
title: "概述（调试接口访问 SDK） | Microsoft Docs"
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
  - "用户定义的类型"
  - ".dbg 文件"
  - "模块"
  - "接口 [DIA SDK]"
  - "DBG 文件"
  - "过程 [DIA SDK]"
  - "可执行文件"
  - "COM 对象，在 DIA SDK 中"
  - "编译单位"
  - "可执行映像"
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 概述（调试接口访问 SDK）
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用 DIA SDK 到 Microsoft 调试信息的访问。  DIA SDK 提供设置的 COM 基于 API 而不必重新编写代码，只要 Microsoft 更改调试信息的形式。  DIA SDK 还允许您从选择读取设置早期版本的调试信息，位于 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 生成的 .pdb 和 .dbg 文件版本 5.0 和更高版本。  
  
 在 DIA SDK 的每个接口表示不同类型的 COM 对象，除此之外，其中否则指定。  附加接口而其他对象，通过显式查询后，例如 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) 或 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)，而不是通过对现有接口指针的 `QueryInterface` 。  
  
## 请参阅  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)