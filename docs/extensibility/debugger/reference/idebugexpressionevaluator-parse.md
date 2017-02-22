---
title: "IDebugExpressionEvaluator::Parse | Microsoft Docs"
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
  - "IDebugExpressionEvaluator::Parse"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::Parse 方法"
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法将表达式字符串转换为分析的表达式。  
  
## 语法  
  
```cpp#  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```c#  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### 参数  
 `upstrExpression`  
 \[in\] 要分析的字符串表达式。  
  
 `dwFlags`  
 \[in\] 的 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) 常数的集合确定表达式如何分析。  
  
 `nRadix`  
 \[in\] 要使用的基数解释任何数字信息。  
  
 `pbstrError`  
 \[out\] 返回错误作为可读的文本。  
  
 `pichError`  
 \[out\] 返回错误的字符位置在表达式字符串。  
  
 `ppParsedExpression`  
 \[out\] 返回在 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 对象进行分析的表达式。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法生成的分析的表达式，而不是实际值。  一个分析的表达式准备进行计算，也就是说，转换为值。  
  
## 请参阅  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)