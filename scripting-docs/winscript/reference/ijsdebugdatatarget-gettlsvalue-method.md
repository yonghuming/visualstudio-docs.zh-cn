---
title: "IJsDebugDataTarget::GetTlsValue 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::GetTlsValue 方法
对于正在调试的线程，请对指定的 TLS 索引检索在线程本地存储 \(TLS\) 槽中的值。  
  
## 语法  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### 参数  
 `threadId`  
 \[in\] 要读取的运行在目标进程中的线程。  
  
 `tlsIndex`  
 \[in\] 当目标进程调用 TlsAlloc 函数时，分配的 TLS 索引。  
  
 `pValue`  
 \[out\] 储存在线程的 TLS 槽中的指针大小的值。  如果目标线程为 32 位，该值的 32 位以上将为零。  
  
## 返回值  
  
## 备注  
 进程中的每个线程都具有自己的针对每个 TLS 索引的槽。  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)