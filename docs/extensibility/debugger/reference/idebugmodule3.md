---
title: "IDebugModule3 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3
helpviewer_keywords: IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95e1c9056b12f1c624a52ee0cf4cbfc8c3272904
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodule3"></a>IDebugModule3
此接口表示一个模块，支持备用位置的符号和 JustMyCode 状态。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口可支持备用位置的符号，并可以使用 JustMyCode 状态 (请参阅[Visual Studio 调试器术语表](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)有关"JustMyCode"的定义)。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)返回此接口。 DE 发送[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)接口的会话调试管理器 (SDM) 的使用[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法。 此外，调用[QueryInterface](/cpp/atl/queryinterface)上[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)接口返回此接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了上的方法[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)接口，此接口实现以下方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|返回的搜索符号和搜索每个路径的结果的路径的列表。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|加载并初始化为当前模块的符号。|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|返回指定模块是否表示用户代码的标志。|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|指定是否模块应视为用户代码或不。|  
  
## <a name="remarks"></a>备注  
 Visual Studio 是此接口的典型使用者。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)