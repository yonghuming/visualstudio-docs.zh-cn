---
title: "IJsDebugDataTarget::FreeVirtualMemory 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::FreeVirtualMemory 方法
释放和\/或解除目标过程虚拟地址空间内的内存区域。  
  
## 语法  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### 参数  
 `address`  
 \[in\] 释放内存的目标进程内的地址。  
  
 `size`  
 \[in\] 要解除的字节数。  若要释放内存区域，此值必须为零。  
  
 `freeType`  
 \[in\] 指示要执行的自由操作的类型。  这通常是 MEM\_RELEASE \(0x8000\)，可释放指定的页面区域。  在执行该操作之后，这些页将处于可用状态。  MEM\_DECOMMIT \(0x4000\) 可用于解除页，无需释放它们。  
  
## 返回值  
  
## 备注  
 有关其他信息，请参阅 VirtualFree Win32 API。  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)