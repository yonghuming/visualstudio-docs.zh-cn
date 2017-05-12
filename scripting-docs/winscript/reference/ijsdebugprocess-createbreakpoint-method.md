---
title: "IJsDebugProcess::CreateBreakPoint 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateBreakPoint
apilocation: jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugProcess::CreateBreakPoint 方法
设置指定的断点文档位置。  
  
## 语法  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### 参数  
 `documentId`  
 \[in\] 指针指向 IDebugDocumentText。  
  
 `characterOffset`  
 \[in\] 与文件开始的字符偏移量。  
  
 `characterCount`  
 \[in\] 中断点应插入文档文本的长度。  
  
 `isEnabled`  
 \[in\] 指定是否能启用断点。  
  
 `ppDebugBreakPoint`  
 \[out\] 表示所创建的断点的对象。  
  
## 返回值  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugProcess 接口](../../winscript/reference/ijsdebugprocess-interface.md)