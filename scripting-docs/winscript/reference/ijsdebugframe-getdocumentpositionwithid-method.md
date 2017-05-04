---
title: "IJsDebugFrame::GetDocumentPositionWithId 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithId
apilocation: jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetDocumentPositionWithId 方法
在用户级别文档中返回此堆栈框架的当前位置。  
  
## 语法  
  
```  
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### 参数  
 `pDocumentId`  
 \[out\] 源文档的唯一 ID（指向 IDebugDocumentText 的指针）。  
  
 `pCharacterOffset`  
 \[out\] 与脚本开头之间的从零开始的字符偏移量。  
  
 `pStatementCharCount`  
 \[out\] 当前语句的长度，从字符中的 \*pCharacterOffset 开始。  
  
## 返回值  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugFrame 接口](../../winscript/reference/ijsdebugframe-interface.md)