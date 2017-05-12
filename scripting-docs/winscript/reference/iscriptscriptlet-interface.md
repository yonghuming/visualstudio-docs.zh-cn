---
title: "IScriptScriptlet 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptScriptlet 接口"
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptScriptlet 接口
对象实现 `IScriptScriptlet` 接口表示事件处理程序脚本。  
  
 除了从 `IScriptEntry` 继承的方法之外，`IScriptScriptlet` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|返回与scriptlet事件的名称。|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|返回与scriptlet的简单事件名称。  这是不包含任何空白的单个符名称。|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|返回在scriptlet的对象承载的完全限定名的最后一个标识符。|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|设置与scriptlet事件的名称。|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|设置与scriptlet的简单事件名称。  这是不包含任何空白的单个符名称。|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|将scriptlet的对象承载的完全限定名的最后一个标识符。|  
  
## 请参阅  
 [活动脚本创作接口](../../winscript/reference/active-script-authoring-interfaces.md)