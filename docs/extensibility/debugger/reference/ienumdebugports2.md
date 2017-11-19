---
title: "IEnumDebugPorts2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPorts2
helpviewer_keywords: IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8379dc1c7dfedfcf46b594fe6ea3bfbc64dfb950
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
此接口枚举的计算机或端口供应商提供的端口。  
  
## <a name="syntax"></a>语法  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 自定义端口供应商提供实现此接口可表示的供应商创建的端口的列表。 Visual Studio 实现此接口支持其自己的端口提供程序。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)以获取此接口，表示的端口供应商创建的端口的列表。 调用[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)获取表示已保存的端口列表此接口到磁盘。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IEnumDebugPorts2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一篇](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|检索指定的数目的枚举序列中的端口。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|跳过指定的数目的枚举序列中的端口。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|将枚举序列重置到开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|创建包含与当前的枚举器相同的枚举状态的枚举。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|获取枚举器中的端口数。|  
  
## <a name="remarks"></a>备注  
 Visual Studio 将使用此接口来帮助填充附加到进程所用端口的列表。  
  
 通常，调试引擎不使用此接口。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)