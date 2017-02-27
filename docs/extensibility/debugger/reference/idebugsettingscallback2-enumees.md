---
title: "IDebugSettingsCallback2::EnumEEs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::EnumEEs"
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugSettingsCallback2::EnumEEs
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

枚举提供的表达式计算器为语言和供应商标识符。  
  
## 语法  
  
```cpp#  
HRESULT EnumEEs(  
   DWORD  celtBuffer,  
   GUID*  rgguidLang,  
   GUID*  rgguidVendor,  
   DWORD* pceltEEs  
);  
```  
  
```c#  
public int EnumEEs(  
   uint       celtBuffer,  
   ref Guid   rgguidLang,  
   ref Guid   rgguidVendor,  
   ref uint[] pceltEEs  
);  
```  
  
#### 参数  
 `celtBuffer`  
 \[in\] 元素数。 `pceltEEs` 缓冲区的。  
  
 `rgguidLang`  
 \[in, out\] 编程语言的唯一标识符。  
  
 `rgguidVendor`  
 \[in, out\] 供应商的唯一标识符。  
  
 `pceltEEs`  
 \[in, out\] 相关表达式计算器。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)