---
title: "VsgDbg 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg 类
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

表示图像诊断的内在组件的编程控制的接口界面。  
  
## 语法  
  
```cpp  
class VsgDbg;  
```  
  
## 成员  
 `VsgDbg` 类提供下列成员。  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[VsgDbg::VsgDbg（构造函数）](../Topic/VsgDbg::VsgDbg%20\(Constructor\).md)|构建 `VsgDbg` 类的实例并选择性准备图形诊断在应用程序的组件来积极捕捉并记录图形信息。|  
|[VsgDbg::~VsgDbg（析构函数）](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|销毁 `VsgDbg` 类的实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[AddMessage](../debugger/addmessage.md)|添加用户信息到图像诊断 HUD \(Head\-Up Display\)。|  
|[BeginCapture](../debugger/begincapture.md)|开始捕捉的时间间隔，于`EndCapture`结束。|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|获取当前帧的其余部分到图像日志文件。|  
|[复制（编程捕获）](../debugger/copy-programmatic-capture.md)|复制有效的图像记录 \(.vsglog\) 文件的内容到新文件。|  
|[EndCapture](../debugger/endcapture.md)|捕捉的时间间隔结尾，从 `BeginCapture` 开始。|  
|[Init](../debugger/init.md)|准备图像诊断的内在组件有效地获取和记录图像信息。|  
|[ToggleHUD](../debugger/togglehud.md)|切换 HUD 的图像诊断打开或关闭。|  
|[UnInit](../debugger/uninit.md)|完成图像日志文件，将其关闭，并且当 app 用来跟踪图像信息时释放使用的资源。|  
  
## 备注  
 `VsgDbg` 类表示你可以用它来控制图形诊断功能编程接口。  你可以使用一些功能，即使你不积极捕捉和记录图形信息，这包括 `AddMessage` 成员函数和 `ToggleHUD` 成员函数。  其他成员函数准备图形诊断的应用程序的组件来启动或停止的图形信息的有效捕捉，或当应用程序积极的捕获或记录图像信息到一个图像日志文件是函数被调用。