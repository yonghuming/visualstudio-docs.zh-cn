---
title: "IDebugPendingBreakpoint2::GetState |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPendingBreakpoint2::GetState
helpviewer_keywords:
- GetState method
- IDebugPendingBreakpoint2::GetState method
ms.assetid: e88d543f-2e83-4ba7-86ca-f874e39955ff
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c3cf3ddb2f210bfa54d70fb68c0bacc5b33aa1dd
ms.lasthandoff: 02/22/2017

---
# <a name="idebugpendingbreakpoint2getstate"></a>IDebugPendingBreakpoint2::GetState
获取挂起断点的状态。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetState(   
   PENDING_BP_STATE_INFO* pState  
);  
```  
  
```c#  
int GetState(   
   PENDING_BP_STATE_INFO[] pState  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pState`  
 [in、 out]一个[PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)结构，其中填充此挂起断点的说明。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回`S_OK`; 否则为返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
