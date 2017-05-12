---
title: "IJsDebugFrame::GetStackRange 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetStackRange 方法
返回逻辑 JavaScript 堆栈帧的绝对地址范围。  
  
## 语法  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### 参数  
 `pStart`  
 \[out\] 与框架的大多数堆栈指针底端对齐。  
  
 `pEnd`  
 \[out\] 与框架的大多数堆栈指针顶端对齐。  
  
## 返回值  
  
## 备注  
 此方法对于拼凑从多个运行时收集的交错堆栈跟踪十分有用  启动和结束堆栈指针能够包含多个实际的计算机堆栈帧（对于已解释的 JavaScript 运行时帧）。当堆栈从高地址扩展到低地址时，启动 \> 结束。  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugFrame 接口](../../winscript/reference/ijsdebugframe-interface.md)