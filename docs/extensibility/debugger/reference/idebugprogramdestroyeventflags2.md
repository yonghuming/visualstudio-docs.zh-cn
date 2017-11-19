---
title: "IDebugProgramDestroyEventFlags2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bee4fe04f22bd9afbff8e2d26ef9d699b0226241
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
允许重写默认行为的调试引擎[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 时结束调试会话。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 此接口由的调试引擎实现。 它可用于可能创建和销毁进程的生存期内的多个程序的主机。  
  
## <a name="methods"></a>方法  
 下表显示的方法`IDebugProgramDestroyEventFlags2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|检索程序销毁标志。|  
  
## <a name="remarks"></a>备注  
 默认行为[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 是以返回到设计模式下，所有程序具有都发送程序后销毁事件。 此接口允许一个调试引擎来更改该行为。  
  
## <a name="requirements"></a>要求  
 标头： Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll