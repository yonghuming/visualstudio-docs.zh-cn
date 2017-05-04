---
title: "IJsDebugProcess::CreateStackWalker 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateStackWalker
apilocation: jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugProcess::CreateStackWalker 方法
堆栈查看器的工厂方法。  
  
## 语法  
  
```  
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### 参数  
 `threadId`  
 \[in\] 线程 ID。  
  
 `ppStackWalker`  
 \[out\] 新的堆栈查看器对象。  
  
## 返回值  
  
## 备注  
 如果线程上没有 JavaScript，则返回 E\_JsDEBUG\_UNKNOWN\_THREAD。  可能只有在停止目标过程后，才能调用此方法。  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugProcess 接口](../../winscript/reference/ijsdebugprocess-interface.md)