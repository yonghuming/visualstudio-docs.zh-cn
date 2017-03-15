---
title: "DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

按其出现定义图像日志文件是否保存到用户的临时文件目录。  
  
## 语法  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## 值  
 通过预处理符号的存在与否决定了图像日志文件是否被保存到用户的临时文件目录。  如果预处理器符号被定义，它的名字被 `VSG_DEFAULT_RUN_FILENAME` 定义，那么文件名是相对于所捕获应用程序的当前目录，或者是一个绝对路径，另外，它的文件名是被 `VSG_DEFAULT_RUN_FILENAME` 定义的，那么他是相对于用户的临时文件目录，不能是绝对路径。  
  
## 备注  
 基于用户的权限，图像日志文件将不能在任意位置保存。  建议您保存图像日志文件到用户的临时文件目录，或其他更好的位置，如果您不确定所选的位置是否可以由用户编写。  
  
 为了防止图像日志文件被保存到临时文件目录日志文件，你必须在包括之前`vsgcapture.h`定义 `DONT_SAVE_VSGLOG_TO_TEMP`。  
  
## 示例  
 此示例演示在主机上如何保存图像日志文件为绝对路径。  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## 请参阅  
 [VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)