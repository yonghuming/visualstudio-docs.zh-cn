---
title: "IDebugPortSupplier3 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 0eb7cf542fa61d53220cd10f54e3fbd7c6165bf4
ms.lasthandoff: 04/05/2017

---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
此接口允许调用方能够确定是否端口供应商可以保留 （通过其写入到磁盘） 的调试器的调用之间的端口，，然后获取这些保留的端口的列表。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 自定义端口供应商提供实现此接口可支持持久保存或保存到磁盘的端口信息。 必须在与相同的对象上实现此接口[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[QueryInterface](/cpp/atl/queryinterface)上`IDebugPortSupplier2`接口，以获得此接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了从继承的方法[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)接口，此接口支持以下︰  
  
|方法|描述|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|返回是否端口提供程序可以调用调试器之间 （通过其写入到磁盘） 中保留端口。|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|返回一个可用于枚举通过编写磁盘的此端口供应商的所有端口的对象。|  
  
## <a name="remarks"></a>备注  
 如果在调用中的端口供应商提供可以保持原样端口，它应实现此接口。 当实例化，并写入磁盘时销毁端口供应商端口供应商应加载端口。  
  
 通常，调试引擎不与端口提供程序交互，并且将具有无需使用此接口。  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
