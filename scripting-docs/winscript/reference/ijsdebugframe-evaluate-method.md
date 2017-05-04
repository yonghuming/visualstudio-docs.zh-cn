---
title: "IJsDebugFrame::Evaluate 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.Evaluate
apilocation: jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::Evaluate 方法
在此堆栈帧的上下文中计算表达式。  
  
## 语法  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### 参数  
 `pExpressionText`  
 \[in\] 要计算的表达式。  
  
 `ppDebugProperty`  
 \[out\] 表示属性浏览器的对象。  
  
 `pError`  
 \[out\] 错误信息，如果发生错误的话。  
  
## 返回值  
  
## 备注  
 返回以下内容：S\_OK：计算成功，\*ppDebugProperty 包含计算结果。  S\_FALSE：计算引发错误（或不支持该计算操作），\*pError 包含错误信息。  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugFrame 接口](../../winscript/reference/ijsdebugframe-interface.md)