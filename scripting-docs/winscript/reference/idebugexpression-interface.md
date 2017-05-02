---
title: "IDebugExpression 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugExpression 接口"
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression 接口
表示异步计算的表达式。  脚本引擎通常实现此接口。  调试器IDE通常使用此接口允许一个立即执行窗口或"监视"窗口。  
  
> [!NOTE]
>  `IDebugExpression` 接口从堆栈帧只能获取。  
  
 除了从 `IUnknown` 继承的方法之外，`IDebugExpression` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|启动该表达式的计算。|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|中止表达式。|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|确定操作是否已完成。|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|当字符串和操作的返回值，则返回表达式的计算结果。|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|在调试特性和操作的返回值，则返回表达式的计算结果。|