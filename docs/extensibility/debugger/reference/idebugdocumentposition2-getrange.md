---
title: "IDebugDocumentPosition2::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetRange"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetRange"
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取此范围文档位置。  
  
## 语法  
  
```cpp#  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### 参数  
 `pBegPosition`  
 \[in, out\] 创建一个起始位置填充的 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) 结构。  ，如果此信息不是必需的，将此参数设置为空值。  
  
 `pEndPosition`  
 \[in, out\] 在结束位置填充的 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) 结构。  ，如果此信息不是必需的，将此参数设置为空值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 为位置断点调试引擎 \(DE\)用于在文档位置指定的范围搜索转发实际上提供代码中的语句。  例如，考虑以下代码：  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 第 5 行不会导致代码正在调试的程序。  如果将该行 5 断点的调试器希望 DE 向前搜索许多提供代码的第一行，调试器将指定包括附加的候选行可能正确设置断点的大小。  DE 通过这些行向前然后将搜索，直到找到了可接受断点的行。  
  
## 请参阅  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)