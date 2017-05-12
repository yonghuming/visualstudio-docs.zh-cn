---
title: "IJsDebugDataTarget::ReadMemory 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadMemory 方法
读取目标过程的内存。  
  
## 语法  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### 参数  
 `address`  
 \[in\] 目标进程的内存的读取基址。  
  
 `flags`  
 \[in\] 控制 ReadMemory 行为的标志。  
  
 `pBuffer`  
 \[out\] 接收来自目标进程的地址空间中的内容的缓冲区。  失败时，此缓冲区内容是未指定的。  
  
 `size`  
 \[in\] 要从进程中读取的字节数。  
  
 `pBytesRead`  
 \[out\] 指示从目标进程读取的字节数。  如果 JsDebugAllowPartialRead 明确，若成功，此值将始终与输入大小完全相等。  如果指定 JsDebugAllowPartialRead，若成功，此值将大于零。  
  
## 返回值  
  
## 备注  
 成功时返回 S\_OK，故障代码用于任何错误。  如果地址无效，则返回 E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS。  有关详情，请参阅 JsDebugAllowPartialRead。  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)