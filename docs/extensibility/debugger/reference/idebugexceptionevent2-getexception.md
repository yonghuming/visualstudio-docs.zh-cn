---
title: "IDebugExceptionEvent2::GetException |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2::GetException
helpviewer_keywords: IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5cc68f7fb843e97e9333aa8d0223ed601df98273
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
获取激发此事件的异常的详细的说明。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```csharp  
int GetException(   
   EXCEPTION_INFO[] pExceptionInfo  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pExceptionInfo`  
 [在中，out][EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)使用异常的说明填充的结构。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 [C + +]调用方负责释放中的任何字符串[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)结构以及释放[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)结构中的对象。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)