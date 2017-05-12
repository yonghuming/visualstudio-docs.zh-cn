---
title: "JS_NATIVE_FRAME 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_NATIVE_FRAME
apilocation: jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JS_NATIVE_FRAME 结构
表示堆栈帧。  
  
## 语法  
  
```  
typedef struct {  
    UINT64 InstructionOffset;  
    UINT64 ReturnOffset;  
    UINT64 FrameOffset;  
    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## 成员  
 `InstructionOffset`  
 指令指针。  
  
 `ReturnOffset`  
 返回地址。  
  
 `FrameOffset`  
 帧指针。  
  
 `StackOffset`  
 堆栈指针。  
  
## 备注  
 `JS_NATIVE_FRAME` 结构由 `IJsStackFrameEnumerator` 使用。  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)