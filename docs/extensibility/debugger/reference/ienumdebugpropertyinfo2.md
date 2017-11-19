---
title: "IEnumDebugPropertyInfo2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPropertyInfo2
helpviewer_keywords: IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e7f261a449e20873183ff59487c1a6b2df6b678
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
此接口枚举[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)结构。  
  
## <a name="syntax"></a>语法  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口可表示的特定属性的信息。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)获取表示特定属性的子级此接口。 调用[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)获取此接口表示一个特定堆栈帧的属性。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IEnumDebugPropertyInfo2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一篇](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|检索指定的数目的[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)枚举序列中的结构。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|跳过指定的数目的[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)枚举序列中的结构。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|将枚举序列重置到开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|创建包含与当前的枚举器相同的枚举状态的枚举。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|获取数[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)枚举器中的结构。|  
  
## <a name="remarks"></a>备注  
 一般情况下，属性是名称、 值、 地址和类型，可以包含的信息，以及适用于关联的属性对象或堆栈帧的任何其他信息的层次结构。 请参阅[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)有关详细信息。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)