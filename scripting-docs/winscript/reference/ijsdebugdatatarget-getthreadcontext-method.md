---
title: "IJsDebugDataTarget::GetThreadContext 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetThreadContext
apilocation: jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::GetThreadContext 方法
检索给定线程的上下文。  
  
## 语法  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### 参数  
 `threadId`  
 \[in\] 运行在目标进程中的线程。  
  
 `contextFlags`  
 \[in\] 指定上下文标志。  这与 CONTEXT 的 ContextFlags 字段相同（有关详细信息，请参阅 winnt.h，搜索 CONTEXT\_ALL。）。  
  
 `contextSize`  
 \[in\] pContext 指定的缓冲区的大小。  
  
 `pContext`  
 \[out\] 接收特定于平台的上下文结构到 pContext 指定的缓冲区。  
  
## 返回值  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)