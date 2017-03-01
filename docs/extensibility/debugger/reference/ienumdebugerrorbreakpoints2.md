---
title: "IEnumDebugErrorBreakpoints2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: 9
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
ms.openlocfilehash: 39b2ce4bb8fdecbe67d6c39e53454e49853f55c8
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
此接口枚举与挂起断点关联的错误断点。  
  
## <a name="syntax"></a>语法  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口作为断点其支持的一部分。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 Visual Studio 调用[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)以获取此界面表示无法绑定的断点的列表或[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)以获取此界面表示未绑定断点的列表。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IEnumDebugErrorBreakpoints2`。  
  
|方法|说明|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|检索指定的数量的错误枚举序列中的断点。|  
|[跳过](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|跳过指定的数目的错误枚举序列中的断点。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|将枚举序列重置到开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|创建包含与当前的枚举数相同的枚举状态的枚举数。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|获取枚举器中的错误断点数。|  
  
## <a name="remarks"></a>备注  
 此接口包含一系列的[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)接口，其中每个描述的断点不能绑定以及为什么它无法绑定。 Visual Studio 将使用`IEnumDebugErrorBreakpoint2`接口，以更新显示在 IDE 中的断点。  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
