---
title: "IDebugThread2::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::SetNextStatement"
helpviewer_keywords: 
  - "IDebugThread2::SetNextStatement"
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

设置当前指令指针到特定代码上下文。  
  
## 语法  
  
```cpp#  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```c#  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### 参数  
 `pStackFrame`  
 保留供将来使用;设置为空值。  
  
 `pCodeContext`  
 \[in\] 描述要执行的代码位置的 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 对象及其上下文。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  下表显示其他可能的值。  
  
|值|说明|  
|-------|--------|  
|不是 E\_CAN \_SET\_NEXT\_STATEMENT\_ON\_NONLEAF\_FRAME|下一个语句不能在堆栈帧深在堆栈帧。|  
|不是 E\_CAN \_SETIP\_TO\_DIFFERENT\_FUNCTION|下一条语句不与堆栈上的任何帧。|  
|不是 E\_CAN \_SET\_NEXT\_STATEMENT\_ON\_EXCEPTION|某些调试引擎不能在异常后设置下一条语句。|  
  
## 备注  
 指令指针指示下一个命令或语句执行。  例如此方法在另一个函数用于重试源代码行或强制继续，。  
  
## 请参阅  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)