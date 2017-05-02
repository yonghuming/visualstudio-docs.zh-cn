---
title: "IEnumDebugStackFrames 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IEnumDebugStackFrames 接口"
ms.assetid: 13484429-0140-4f4f-8502-3ca2a0553ed4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames 接口
枚举堆栈帧与线程相对应。  
  
## 方法  
 除了从 `IUnknown` 继承的方法之外，`IEnumDebugStackFrames` 接口还公开下面的方法。  
  
|方法|说明|  
|--------|--------|  
|[IEnumDebugStackFrames::Next](../../winscript/reference/ienumdebugstackframes-next.md)|检索枚举序列中指定数目的段。|  
|[IEnumDebugStackFrames::Skip](../../winscript/reference/ienumdebugstackframes-skip.md)|跳过枚举序列中指定数目的段。|  
|[IEnumDebugStackFrames::Reset](../../winscript/reference/ienumdebugstackframes-reset.md)|将枚举序列重置到开始处。|  
|[IEnumDebugStackFrames::Clone](../../winscript/reference/ienumdebugstackframes-clone.md)|创建与当前枚举器包含相同状态的一个枚举器。|