---
title: "IDebugStackFrameSniffer 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSniffer 接口"
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSniffer 接口
提供一种枚举元素已知的逻辑堆栈帧。  脚本引擎通常实现此接口。  进程内调试管理器使用此接口查找所有堆栈帧与特定线程。  
  
> [!NOTE]
>  调试器调用此接口从线程相关的内部。  脚本引擎必须识别当前线程并返回适当的枚举器。  
  
## 方法  
 除了从 `IUnknown` 继承的方法之外，`IDebugStackFrameSniffer` 接口还公开下面的方法。  
  
|方法|说明|  
|--------|--------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|返回堆栈帧的枚举数当前线程的。|