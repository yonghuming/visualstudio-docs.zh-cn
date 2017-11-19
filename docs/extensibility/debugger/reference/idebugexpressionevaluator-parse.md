---
title: "IDebugExpressionEvaluator::Parse |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluator::Parse
helpviewer_keywords: IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0491cd6d80db449fbeaa8fee2a6040a66082558
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
此方法将一个表达式字符串转换为一个已分析的表达式。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>参数  
 `upstrExpression`  
 [in]要分析的表达式字符串。  
  
 `dwFlags`  
 [in]集合[PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)确定如何表达式是，无法被分析的常量。  
  
 `nRadix`  
 [in]要用于解释的任何数字信息的基数。  
  
 `pbstrError`  
 [out]为用户可读文本将返回错误。  
  
 `pichError`  
 [out]在表达式字符串中返回的错误开始的字符位置。  
  
 `ppParsedExpression`  
 [out]返回中的已分析的表达式[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 此方法生成的已分析的表达式，而不是一个实际值。 分析的表达式已准备好进行计算，即，转换为值。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)