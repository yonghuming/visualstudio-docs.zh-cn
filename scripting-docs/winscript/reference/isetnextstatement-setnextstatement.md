---
title: "ISetNextStatement::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISetNextStatement.SetNextStatement
apilocation: scrobj.dll
ms.assetid: c5534f3b-39a5-4466-b8fc-69b717c6eee9
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ISetNextStatement::SetNextStatement
此方法将更新脚本解释器可以执行的代码上下文。  
  
## 语法  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### 参数  
 `pStackFrame`  
 \[out\]一个指向堆栈帧对象的指针。  
  
 `pCodeContext`  
 \[out\]一个指向代码上下文对象的指针。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [ISetNextStatement 接口](../../winscript/reference/isetnextstatement-interface.md)