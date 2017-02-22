---
title: "IDiaFrameData::execute | Microsoft Docs"
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
  - "IDiaFrameData::execute 方法"
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

执行展开的堆栈并返回该堆栈审核帧接口的结果。  
  
## 语法  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### 参数  
 `frame`  
 \[in\] 保存帧寄存器状态的 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  下表显示可能返回此方法的值。  
  
|值|说明|  
|-------|--------|  
|E\_DIA\_INPROLOG|未能执行堆栈帧，在序言码时。|  
|E\_DIA\_SYNTAX|在帧程序遇到的分析错误。|  
|E\_DIA\_FRAME\_ACCESS|无法访问注册或内存。|  
|E\_DIA\_VALUE|在求值 \(例如，被零除的错误\)。|  
  
## 备注  
 此方法调用在调试过程中展开堆栈。  [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) 对象由客户端应用程序接收更新注册并提供 `execute` 方法的方法实现。  
  
## 请参阅  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)