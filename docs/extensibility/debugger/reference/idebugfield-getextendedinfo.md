---
title: "IDebugField::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugField::GetExtendedInfo 方法"
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法扩展有关字段的信息。  
  
## 语法  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```c#  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### 参数  
 `guidExtendedInfo`  
 \[in\] 选择信息返回。  有效值为：  
  
|值|说明|  
|-------|--------|  
|`guidConstantValue`|值作为字节序列。|  
|`guidConstantType`|类型作为类型签名。|  
  
 `prgBuffer`  
 \[out\] 返回扩展信息。  
  
 `pdwLen`  
 \[in, out\] 返回扩展的信息的大小，以字节为单位\)。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 目前，此方法返回常数类型的或值。  调用方必须释放在 `prgBuffer` 返回的缓冲区通过调用 COM 的 `CoTaskMemFree` 函数 \(C\+\+\) 或 <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> \(c\#\)。  
  
## 请参阅  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)