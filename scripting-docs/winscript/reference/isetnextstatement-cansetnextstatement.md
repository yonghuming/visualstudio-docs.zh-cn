---
title: "ISetNextStatement::CanSetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISetNextStatement.CanSetNextStatement
apilocation: scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# ISetNextStatement::CanSetNextStatement
此方法确定执行点是否，确定正在执行的代码下一条语句，可以设置为指定的位置。  
  
## 语法  
  
```  
HRESULT CanSetNextStatement(  
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
|`S_OK`|下一条语句可以将更新到指定的代码上下文。|  
|`S_FALSE`|下一条语句不能更新到指定的代码上下文。|  
  
## 备注  
  
## 请参阅  
 [ISetNextStatement 接口](../../winscript/reference/isetnextstatement-interface.md)