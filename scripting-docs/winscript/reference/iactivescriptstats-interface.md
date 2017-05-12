---
title: "IActiveScriptStats 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptStats 接口"
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats 接口
允许宿主查询正在运行的脚本的统计信息。  宿主可以使用这些信息确定脚本是否花费太长时间完成。  
  
 除了从 `IUnknown` 继承的方法之外，`IActiveScriptStats` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|返回一个标准脚本统计信息。|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|返回一个自定义脚本统计信息。|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|重置此脚本的统计信息。|