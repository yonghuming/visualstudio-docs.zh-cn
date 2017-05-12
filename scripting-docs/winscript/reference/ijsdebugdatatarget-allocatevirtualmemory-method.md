---
title: "IJsDebugDataTarget::AllocateVirtualMemory 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.AllocateVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::AllocateVirtualMemory 方法
释放和\/或提交目标过程虚拟地址空间内的内存区域。  
  
## 语法  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### 参数  
 `address`  
 \[in\] 提交或保留内存的目标进程内的地址。  此值通常为零，在这种情况下，系统会选择地址。  
  
 `size`  
 \[in\] 要分配的内存区域的大小（以字节为单位）。  系统将自动计算到下一页边界。  
  
 `allocationType`  
 \[in\] 指示要执行的分派类型。  这通常是 MEM\_COMMIT &#124; MEM\_RESERVE \(0x3000\)，可一步完成保留和提交分配。  
  
 `pageProtection`  
 \[in\] 要分配的页面区域的内存保护。  如果已提交页面，则可以指定任意一个内存保护常数（例如，PAGE\_READWRITE、PAGE\_EXECUTE）。  
  
 `pAllocatedAddress`  
 \[out\] 页分配的区域的基址。  
  
## 返回值  
  
## 备注  
 除非使用 MEM\_RESET，该函数将分配的内存初始化为零。  有关其他信息，请参阅 VirtualAlloc Win32 API。  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)