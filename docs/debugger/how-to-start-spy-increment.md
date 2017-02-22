---
title: "How to: Start Spy++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Spy++, starting"
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Start Spy++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以从 Visual Studio 或在命令提示符处启动 Spy\+\+。  
  
 在启动 Spy\+\+ 时，如果显示一条表示需要权限才能更改计算机的消息，请单击**“是”**。  
  
> [!NOTE]
>  只能运行 Spy\+\+ 的一个实例。  如果尝试运行其他实例，则会使当前正在运行的实例获取焦点。  
  
### 从 Visual Studio 启动 Spy\+\+  
  
-   在**“工具”**菜单上，单击**“Spy\+\+”**。  
  
     由于 Spy\+\+ 是单独运行的，因此您在启动它后可关闭 Visual Studio。  
  
    > [!NOTE]
    >  在使用 Spy\+\+ 记录消息时，可能会导致操作系统的运行速度更慢。  
  
### 从命令提示符处启动 Spy\+\+  
  
1.  在命令提示符窗口中，将目录更改为包含 spyxx.exe 的文件夹。  通常，此文件夹的路径为 ..  \\*Visual Studio 安装文件夹*\\Common7\\Tools\\。  
  
2.  键入 **spyxx.exe**，然后按 Enter。  
  
## 请参阅  
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)