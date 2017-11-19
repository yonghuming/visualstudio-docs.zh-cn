---
title: "IDebugPropertyCreateEvent2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPropertyCreateEvent2
helpviewer_keywords: IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afe91b8dfa6321d046b7bdeb301e426d1083263f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
创建与特定文档相关联的属性时，此接口是由的调试引擎 (DE) 发送到会话调试管理器 (SDM) 中。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 DE 实现此接口来报告已创建了一个属性。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)接口必须实现该接口对同一个对象。 SDM 使用[QueryInterface](/cpp/atl/queryinterface)访问`IDebugEvent2`接口。 如果 DE 已创建与已加载或创建的脚本关联的属性，而该脚本需要出现在 IDE 中，被实现此接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 DE 创建，并将此事件对象发送到报表创建属性。 通过使用发送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM 时将其附加到正在调试的程序提供的回调函数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugPropertyCreateEvent2`接口。  
  
|方法|描述|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|获取新的属性。|  
  
## <a name="remarks"></a>备注  
 如果属性具有特定文档或与之关联的脚本，DE 可以此将事件发送至 SDM 以更新**脚本文档**窗口与文档的名称。 将调用 SDM [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)具有自变量`guidDocument`检索`VARIANT`包含[IUnknown](/cpp/atl/iunknown)指针。 将调用 SDM [QueryInterface](/cpp/atl/queryinterface)上检索此指针[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)接口用于更新**脚本文档**窗口。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)