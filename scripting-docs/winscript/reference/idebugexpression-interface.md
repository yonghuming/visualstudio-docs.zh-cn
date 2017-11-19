---
title: "IDebugExpression 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39e139e09362fc392d1110e26837c52fd4c642c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpression-interface"></a>IDebugExpression 接口
表示异步计算的表达式。 脚本引擎通常实现此接口。 调试器 IDE 通常使用此接口来启用立即执行窗口或监视窗口。  
  
> [!NOTE]
>  `IDebugExpression`接口则仅可从堆栈帧。  
  
 除了从继承的方法`IUnknown`、`IDebugExpression`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|开始对表达式求值。|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|中止表达式。|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|确定操作是否完成。|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|返回一个字符串，以及操作的返回值的表达式计算的结果。|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|返回为调试属性和操作的返回值的表达式计算的结果。|