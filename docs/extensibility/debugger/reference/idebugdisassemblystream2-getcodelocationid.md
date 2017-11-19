---
title: "IDebugDisassemblyStream2::GetCodeLocationId |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords: IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2757130ec88cee8d9bdfe28008a8e19834f9f8fb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
返回特定代码上下文的代码位置标识符。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)对象转换为标识符。  
  
 `puCodeLocationId`  
 [out]返回的代码位置标识符。 请参阅“备注”。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。 返回`E_CODE_CONTEXT_OUT_OF_SCOPE`代码上下文是否有效，但的范围之外。  
  
## <a name="remarks"></a>备注  
 代码位置标识符是特定于支持反汇编的调试引擎 (DE)。 此位置标识符由内部 DE 来跟踪代码中的位置，并通常是地址或某种类型的偏移量。 唯一要求是，如果一个位置的代码上下文小于另一个位置的代码上下文则相应的代码位置标识符的第一个代码上下文还必须是小于第二个代码上下文的代码位置标识符。  
  
 若要检索的代码位置标识符的代码上下文，调用[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)