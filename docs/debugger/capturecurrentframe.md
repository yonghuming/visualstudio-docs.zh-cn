---
title: "CaptureCurrentFrame | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CaptureCurrentFrame
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

获取当前帧的其余部分到图像日志文件。  
  
## 语法  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## 备注  
 如果另一个捕捉正在进行中，例如由 `BeginCapture` 函数开始捕获，那么捕获完成并作为一个独特的框架记录到日志的图形。  跟着，图像诊断开始捕获当前帧的其余部分，被记录为不同的框架。  当前帧结束的地方标记为调用当前。  
  
 想要捕捉帧，你必须准备你的app来捕捉并且记录图像信息，你必须在你调用 `CaptureCurrentFrame` 或前代替 `VsgDbg` 调用 [Init](../debugger/init.md)。  
  
## 请参阅  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)