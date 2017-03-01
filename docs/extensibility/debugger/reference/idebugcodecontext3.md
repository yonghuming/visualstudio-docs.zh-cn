---
title: "IDebugCodeContext3 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: da2e6011171afab54a055317c1ee9dc807200a02
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
扩展[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)接口，以使模块和处理接口的检索。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 由调试器引擎实现，并且由[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]调试包。  
  
## <a name="methods"></a>方法  
 除了上方法`IDebugCodeContext2`接口，此接口实现的以下方法︰  
  
|方法|说明|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|检索到的调试模块接口的引用。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|检索到调试进程的接口的引用。|  
  
## <a name="remarks"></a>备注  
 这是通常不需要实现的可选接口。  
  
## <a name="requirements"></a>要求  
 标头︰ Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll
