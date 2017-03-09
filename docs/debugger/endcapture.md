---
title: "EndCapture | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# EndCapture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

捕捉的时间间隔结尾，从 `BeginCapture` 开始。  
  
## 语法  
  
```cpp  
void EndCapture();  
```  
  
## 备注  
 获取间隔通常跨越一个帧的子集，例如，当您仅捕获了有关特定类型的绘制调用的图像信息。  如果捕获区间跨越调用存在，则图形信息两帧被捕获。  第一帧跨越调用 `BeginCapture` 和调用当前之间的间隔，第二帧跨越调用第一个Direct3D的事件在调用当前和调用 `EndCapture` 之后。  
  
 想要捕捉间隔，你必须准备你的app来捕捉并且记录图像信息，你必须在你调用 `BeginCapture` 或 `EndCapture` 前代替 `VsgDbg` 调用 [Init](../debugger/init.md)。  
  
## 请参阅  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)