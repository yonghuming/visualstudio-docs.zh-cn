---
title: "IEnumJsStackFrames::Next 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumJsStackFrames.Next
apilocation: jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumJsStackFrames::Next 方法
获取帧的指定的数。  
  
## 语法  
  
```  
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### 参数  
 `cFrameCount`  
 \[in\] 要获取的框架数。  
  
 `pFrames`  
 \[out\] 用于存储帧的数组。  
  
 `pcFetched`  
 \[out\] 返回的帧数。  
  
## 返回值  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IEnumJsStackFrames 接口](../../winscript/reference/ienumjsstackframes-interface.md)