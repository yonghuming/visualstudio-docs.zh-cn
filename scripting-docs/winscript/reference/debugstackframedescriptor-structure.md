---
title: "DebugStackFrameDescriptor 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugStackFrameDescriptor
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugStackFrameDescriptor 结构"
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DebugStackFrameDescriptor 结构
枚举堆栈帧并将几个枚举器的输出同一线程上。  
  
## 语法  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## 成员  
 `pdsf`  
 堆栈帧对象。  
  
 `dwMin`  
 物理地址的下半部分范围的计算机相关的表示形式与此堆栈帧。  
  
 `dwLim`  
 物理地址的上限之间的一个设备相关的表示形式与此堆栈帧。  
  
 `fFinal`  
 标记指示框架处理。  
  
 `punkFinal`  
 如果此参数不是 `NULL`，当前枚举数组合应停止，并且应开始新的。  对象指示如何开始新的枚举。  
  
## 备注  
 进程内调试管理器使用此结构排序从多个脚本引擎的堆栈帧。  按照约定，堆栈增加速率。  因此，在堆栈长大的体系结构，应添加两个地址。  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)