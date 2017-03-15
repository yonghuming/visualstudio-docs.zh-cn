---
title: "Init | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Init
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在应用程序的组成部分准备图形诊断，积极捕捉和记录的图形信息图形日志文件。  
  
## 语法  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### 参数  
 `vsgLogGetter`  
 可调用实体，如函数，函数指针，lambda，或函数对象，可以接受参数是一个组成`wchar_t`缓冲区的长度与指向的缓冲区的指针，并返回`void`。  调用时，可调用的实体确定将用于记录图像信息的文件名和在返回之前写入到指定缓冲区。  
  
## 备注  
 当 `VsgDbg` 类的实例由指定的 `bDefaultInit` 构造参数像 `true`，则 `Init` 函数自动被调用；否则，在你积极地捕获和记录图像信息前，`Init` 必须显式被调用。  
  
 你可以通过调用 `UnInit` 最终关闭激活图形日志文件，然后按再次调用 `Init` 捕捉和记录更多的图像信息到一个新的图形日志文件。  你可以重复使用同一个 `VsgDbg` 实例来创建几个独立的图像日志文件。  
  
## 请参阅  
 [UnInit](../debugger/init.md)