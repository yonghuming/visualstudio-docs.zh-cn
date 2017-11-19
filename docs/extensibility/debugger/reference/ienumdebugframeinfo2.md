---
title: "IEnumDebugFrameInfo2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugFrameInfo2
helpviewer_keywords: IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c9c0cd58c069989b9516d707ba4c9a35faf53013
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
此接口枚举[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)结构。  
  
## <a name="syntax"></a>语法  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口可提供一份结构描述当前调用堆栈。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 Visual Studio 调用[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)若要获取此接口时断点，异常，异常终止在中发生或正在调试的程序。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IEnumDebugFrameInfo2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一篇](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|检索指定的数目的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)枚举序列中的结构。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|跳过指定的数目的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)枚举序列中的结构。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|将枚举序列重置到开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|创建包含与当前的枚举器相同的枚举状态的枚举。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|获取数[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)枚举器中的结构。|  
  
## <a name="remarks"></a>备注  
 Visual Studio 将获取此接口来处理断点、 异常或用户生成的暂停正在调试的程序上的第一步。 列表[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)结构表示当前的调用堆栈，并指定当前位于开头的列表以及最旧的函数的函数调用的调用列表的末尾。 每个`FRAMEINFO`表示堆栈帧，在其中可以计算表达式并查看本地变量的上下文。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)