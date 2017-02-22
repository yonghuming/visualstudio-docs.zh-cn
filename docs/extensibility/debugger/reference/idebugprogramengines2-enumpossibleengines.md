---
title: "IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs"
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
  - "IDebugProgramEngines2::EnumPossibleEngines"
helpviewer_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回所有可能的 GUID 调试能 \(DE\)调试此过程的引擎。  
  
## 语法  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```c#  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### 参数  
 `celtBuffer`  
 \[in\] DE 返回的 GUID 的数字。  它还指定 `rgguidEngines` 数组的最大大小。  
  
 `rgguidEngines`  
 \[in, out\] 数组、将填充的 GUID。  
  
 `pceltEngines`  
 \[out\] 返回 DE 返回的 GUID 的实际数目。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  返回 \[c\+\+\] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` 或 \[c\#\] 0x8007007A，如果缓冲区不足够大。  
  
## 备注  
 为了确定有多少个引擎一次是，调用此方法与 `celtBuffer` 参数设置为 0 `rgguidEngines` 参数设置为空值。  这将返回 `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` \(C\# 中 0x8007007A\)，并且， `pceltEngines` 参数返回缓冲区的所需大小。  
  
## 请参阅  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)