---
title: "IJsDebugFrame::GetDocumentPositionWithName 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetDocumentPositionWithName 方法
在用户级别文档中返回此堆栈框架的当前位置。  
  
## 语法  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### 参数  
 `pDocumentName`  
 \[out\] 用于静态脚本，文档的 URL。  针对动态脚本，将把包含脚本类型（例如，eval 代码，函数代码等）的名称返回。  
  
 `pLine`  
 \[out\] 从第一行开始的行在文档中的位置。  
  
 `pColumn`  
 \[out\] 从第一行开始的行在文档中的位置。  
  
## 返回值  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugFrame 接口](../../winscript/reference/ijsdebugframe-interface.md)