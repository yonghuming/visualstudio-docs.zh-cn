---
title: "ISetNextStatement 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ISetNextStatement 接口
此接口由解释器实现允许进程调试管理器来更新当前语句。  它从堆栈帧对象上实现，并且，PDM通过QI获取此接口。  
  
 接口提供设置执行非常有用的点，确定要执行的下一条语句的方法。  
  
 除了从 `IUnknown` 继承的方法之外，`ISetNextStatement` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|确定执行点是否可以设置为指定的位置。|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|设置执行点指定的位置。|