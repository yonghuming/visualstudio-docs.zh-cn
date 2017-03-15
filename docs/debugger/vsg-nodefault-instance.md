---
title: "VSG_NODEFAULT_INSTANCE | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定义了它是否存在的默认的 [VsgDbg 类](../debugger/vsgdbg-class.md) 实例类，它提供了纲领性的捕获接口。  
  
## 语法  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## 值  
 按预定于符号存在与否决定 `VsgDbg` 类默认实例是否被提供。  如果符号被定义，则不提供 `VsgDbg` 类的默认实例，否则，一个提供默认实例并初始化。  
  
 通过一个指针提供编程捕捉接口，指针具有全局范围，`g_pVsgDbg`。  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## 备注  
 默认实例通常是足够的，但是要使用在 DLL 中的编程接口捕获在该 DLL 之外创建的 D3D 设备时，你必须创建和管理自己的 `VsgDbg` 实例类。  如果你用这种方法你自己的界面管理编程捕捉接口，被定义的 `VSG_NODEFAULT_INSTANCE` 默认实例是禁用的，避免开销。  
  
 如果默认值实例不是禁用的，在程序运行前它自动初始化，并当程序的末尾时自动销毁。  您不必显式的初始化或不初始化此实例。  
  
 禁用默认的实例，你必须在你的程序中包括 `vsgcapture.h` 前定义 `VSG_NODEFAULT_INSTANCE`。  
  
## 示例  
 此示例演示如何禁用默认实例：  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```