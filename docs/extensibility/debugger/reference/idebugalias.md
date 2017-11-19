---
title: "IDebugAlias |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias
helpviewer_keywords: IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 128dc9001faba06b1c95c5ebc364f319891ce409
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 表示变量的数值别名。 别名是只需为变量指定其他名称。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 表达式计算器 (EE) 实现此接口可支持变量数字别名。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)创建特定对象的别名。 若要搜索的别名，请使用[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)或[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 以下方法定义中`IDebugAlias`接口。  
  
|方法|描述|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|获取此别名所引用的对象。|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|获取别名名称。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|检索`ICorDebugValue`接口提供对访问托管代码对此对象 （仅适用于托管代码） 的信息。|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|将此标记别名为不再使用。|  
  
## <a name="remarks"></a>备注  
 别名是 # 字符，例如，&#1001; 后跟的字符串形式的十进制数字。  
  
## <a name="requirements"></a>要求  
 标头： ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [表达式评估接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)