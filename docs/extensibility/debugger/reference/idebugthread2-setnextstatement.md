---
title: "IDebugThread2::SetNextStatement |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::SetNextStatement
helpviewer_keywords: IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6dd345fe298af42a69ac076bf92de7df9db82ec2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
将当前指令指针设置为给定的代码上下文。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pStackFrame`  
 留待将来使用;设置为 null 值。  
  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)对象，描述将要执行的代码位置和其上下文。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。 下表显示其他可能的值。  
  
|值|描述|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|下一个语句不能为更深入地帧堆栈上的堆栈帧中。|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|下一条语句与堆栈中的任何帧无关。|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|一些调试引擎不能设置在出现异常之后的下一个语句。|  
  
## <a name="remarks"></a>备注  
 指令指针指示的下一步的指令或语句，以执行。 若要重试代码的源代码行，或若要强制执行继续在另一个函数，例如，使用此方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)