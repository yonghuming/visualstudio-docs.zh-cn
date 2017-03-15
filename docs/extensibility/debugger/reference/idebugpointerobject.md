---
title: "IDebugPointerObject |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
caps.latest.revision: 11
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
ms.openlocfilehash: ad0660d583e1bc23c19b0fbd1836eb952d778665
ms.lasthandoff: 02/22/2017

---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口表示指针对象。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 表达式计算器实现此接口来表示指针对象。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)接口通过使用可以获得此接口[QueryInterface](/visual-cpp/atl/queryinterface)如果`IDebugObject`表示的指针。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了从继承的方法[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)、`IDebugPointerObject`接口公开下列方法。  
  
|方法|说明|  
|------------|-----------------|  
|[取消引用](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|获取指向该接口的对象。|  
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|获取该接口指向作为一系列连续的字节的值。|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|设置该接口指向一系列连续字节中的值。|  
  
## <a name="remarks"></a>备注  
 表达式计算器使用此接口来表示分析树中的指针。  
  
## <a name="requirements"></a>要求  
 标头︰ ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
