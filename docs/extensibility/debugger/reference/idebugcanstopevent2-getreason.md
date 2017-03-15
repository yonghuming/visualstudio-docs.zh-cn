---
title: "IDebugCanStopEvent2::GetReason |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 11
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
ms.openlocfilehash: d6b75ff3e3fc74018bb8f17d7754183309ea39c3
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
获取调试引擎 (DE) 是为什么想要停止的原因。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```c#  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pcr`  
 [out]返回一个介于[CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)介绍了此事件的原因的枚举。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 这种方法通常称为之前[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)方法，以便调用方可以确定是否将传递非零值 (`TRUE`) 到`IDebugCanStopEvent2::CanStop`方法。  
  
 停止的原因可能是`CANSTOP_ENTRYPOINT`，这意味着 DE 已达到入口点，或`CANSTOP_STEPIN`，这意味着 DE 单步执行函数。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
