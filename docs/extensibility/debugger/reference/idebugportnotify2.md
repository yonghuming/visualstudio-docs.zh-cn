---
title: "IDebugPortNotify2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortNotify2
helpviewer_keywords: IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9aec1465334a4399136d47c29faa8cccbb99c3a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
此接口注册或注销可以使用的端口运行调试程序。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 自定义端口供应商提供实现此接口以支持添加和删除与该端口的程序。 它通常实现上实现的相同对象[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[QueryInterface](/cpp/atl/queryinterface)上`IDebugPort2`接口返回此接口。 此外，调用[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)返回此接口。 调试引擎可以看到此接口作为参数传递给[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugPortNotify2`。  
  
|方法|描述|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|注册的端口运行，它可调试的程序。|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|注销要调试从其运行的端口的程序。|  
  
## <a name="remarks"></a>备注  
 除非调试端口都具有任何方法知道程序将加载或卸载时，自定义端口提供程序必须实现此接口。 使用此接口跟踪为通过特定端口调试加载的所有程序。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)