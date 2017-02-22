---
title: "IDebugDocumentContext2::GetSourceRange | Microsoft Docs"
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
  - "IDebugDocumentContext2::GetSourceRange"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetSourceRange"
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取此的源代码大小文档上下文。  
  
## 语法  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetSourceRange(   
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
 源范围是源代码的整个范围，从当前语句返回到以前的声明后面提供的代码。  源范围为混合的源语句通常使用，包括注释，并且代码 " 反汇编 " 窗口。  
  
 此内包含的代码语句的范围文档上下文的访问，调用 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) 方法。  
  
## 请参阅  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)