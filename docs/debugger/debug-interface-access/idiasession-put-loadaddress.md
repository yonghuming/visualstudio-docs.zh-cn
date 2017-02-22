---
title: "IDiaSession::put_loadAddress | Microsoft Docs"
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
  - "IDiaSession::put_loadAddress 方法"
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

设置对应于符号此符号存储的可执行文件的加载地址。  
  
## 语法  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### 参数  
 `NewVal`  
 \[in\] 可执行文件的加载地址。  
  
## 备注  
 使用此方法，的 \(VA\)值符号虚拟地址属性求值。  ，除非此属性设置为非零，虚拟地址不是数字。  
  
> [!NOTE]
>  必须调用此方法，当获取 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 对象，因此，在开始使用对象之前是否需要使用该符号任何虚拟属性。  
  
## 请参阅  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)