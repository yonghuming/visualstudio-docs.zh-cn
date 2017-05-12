---
title: "IJsDebugDataTarget::CreateStackFrameEnumerator 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.CreateStackFrameEnumerator
apilocation: jscript9diag.dll
ms.assetid: cda172e5-18d0-43c5-81d8-432ab30ee70d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::CreateStackFrameEnumerator 方法
创建堆栈帧的枚举器。  
  
## 语法  
  
```  
HRESULT CreateStackFrameEnumerator(  
   DWORD threadId,  
   IEnumJsStackFrames **ppEnumerator  
);  
```  
  
#### 参数  
 `threadId`  
 \[in\] 运行在目标进程中的线程。  
  
 `ppEnumerator`  
 \[out\] 堆栈帧的枚举器。  
  
## 返回值  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)