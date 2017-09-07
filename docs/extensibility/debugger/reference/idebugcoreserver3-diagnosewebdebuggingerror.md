---
title: "IDebugCoreServer3::DiagnoseWebDebuggingError |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 8
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2c9ed64c1db1472e334333f3c2cb6d1bfb017c25
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
尝试确定为何 auto-attach 失败。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pszUrl`  
 [in]当前未使用;应始终设置为 null 值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。 以下是其他典型的返回代码：  
  
|代码|描述|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|无法确定远程服务器开始调试失败的原因。|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|在远程服务器上，可能是由于权限不足而无法调试或因为未启用 DEBUG 谓词。|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Web 服务器已被锁定，正在阻塞 DEBUG 谓词，需要启用调试。|  
  
## <a name="see-also"></a>另请参阅  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
