---
title: "IJsDebugStackWalker::GetNext 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugStackWalker.GetNext
apilocation: jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugStackWalker::GetNext 方法
获取下一帧。  
  
## 语法  
  
```  
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### 参数  
 `ppFrame`  
 \[out\] 表示堆栈帧的对象。  
  
## 返回值  
  
## 备注  
 当不再有将要枚举的堆栈帧时，返回 E\_JsDEBUG\_OUTSIDE\_OF\_VM  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugStackWalker 接口](../../winscript/reference/ijsdebugstackwalker-interface.md)