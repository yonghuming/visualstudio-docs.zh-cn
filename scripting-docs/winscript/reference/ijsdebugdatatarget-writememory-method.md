---
title: "IJsDebugDataTarget::WriteMemory 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::WriteMemory 方法
读取目标过程的内存。  
  
## 语法  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### 参数  
 `address`  
 \[in\] 目标进程的内存的写入基址。  
  
 `pMemory`  
 \[in\] 要写入指定进程的地址空间的数据。  
  
 `size`  
 \[in\] 要写入进程中的字节数。  
  
## 返回值  
  
## 备注  
 在传输数据之前，系统会验证在基址和指定大小的内存中的全部数据是否能访问，如果不能访问，该函数就会引发 E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS 错误。  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)