---
title: "IDebugModule3::SetJustMyCodeState |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugModule3::SetJustMyCodeState
helpviewer_keywords:
- IDebugModule3::SetJustMyCodeState
ms.assetid: 68f8166d-ef64-49ae-ad5e-79604f43bbd4
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
ms.openlocfilehash: 4fd680371b20b12e3e8ed5a1c8991eb35a1cb51f
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmodule3setjustmycodestate"></a>IDebugModule3::SetJustMyCodeState
将标记或不视为用户代码模块。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT SetJustMyCodeState(  
   BOOL fIsUserCode  
);  
```  
  
```c#  
int SetJustMyCodeState(  
   int fIsUserCode  
);  
```  
  
#### <a name="parameters"></a>参数  
 `fIsUserCode`  
 [in]非零 (`TRUE`) 如果模块应被视为用户代码，零 (`FALSE`) 如果不应。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回`S_OK`; 否则为将返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
