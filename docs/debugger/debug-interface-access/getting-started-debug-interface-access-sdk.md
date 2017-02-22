---
title: "入门（调试接口访问 SDK） | Microsoft Docs"
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
  - ".dbg 文件"
  - "DBG 文件"
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 入门（调试接口访问 SDK）
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

调试界面访问 \(DIA\) SDK 将指导文档和说明如何使用 DIA API 的示例可供您使用。  使用接口和方法。 DIA SDK 开发打开 .pdb 和 .dbg 文件并搜索其内容符号、值、属性、地址和其他调试信息的自定义应用程序。  此 SDK 还提供了引用属性的表与 C\+\+ 应用程序中的符号。  
  
 为获得最佳使用 DIA SDK，您应当熟悉以下操作:  
  
-   C\+\+ 编程语言  
  
-   COM 编程  
  
-   生成的示例 \(IDE\) Visual Studio 集成开发环境  
  
 DIA SDK 通常会随 Visual Studio 一起安装，并且其默认位置为 *\[drivers\]*\\Program Files\\Microsoft Visual Studio 9.0\\DIA SDK。  作为安装的一部分， msdia90.dll，实现 DIA SDK，自动注册需要执行使用它包括 `dia2.h` 在过程以及指向 `diaguids.lib`的因此所有。  
  
 标题:include \\ dia2.h  
  
 库:lib \\ diaguids.lib  
  
 DLL:bin \\ msdia80.dll  
  
 IDL:IDL \\ dia2.idl  
  
## 本节内容  
 [概述](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 检查 DIA. 基本结构。  
  
 [查询 .Pdb 文件](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 的分步说明有关如何使用 DIA API 查询 .pdb 文件。  
  
## 请参阅  
 [调试接口访问 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)