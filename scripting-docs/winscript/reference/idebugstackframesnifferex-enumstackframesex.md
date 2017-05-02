---
title: "IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx::EnumStackFramesEx"
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSnifferEx::EnumStackFramesEx
返回堆栈帧的枚举数当前线程的。  
  
## 语法  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### 参数  
 `dwSpMin`  
 \[in\]枚举的堆栈帧较低的地址限制。  
  
 `ppedsf`  
 \[in\]堆栈帧的枚举数当前线程的。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 堆栈帧枚举数返回启动位于堆栈顶部的框架，与最近驱动器的帧。  枚举数包含地址大于或等于 `dwSpMin`的仅堆栈帧。  
  
## 请参阅  
 [IDebugStackFrameSnifferEx 接口](../../winscript/reference/idebugstackframesnifferex-interface.md)