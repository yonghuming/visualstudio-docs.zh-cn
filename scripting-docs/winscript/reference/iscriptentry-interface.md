---
title: "IScriptEntry 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptEntry 接口"
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry 接口
对象 `IScriptEntry` 接口表示任何脚本的实现块或函数对象。  
  
 除了从 `IScriptNode` 继承的方法之外，`IScriptEntry` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|返回对应于 `IScriptEntry` 脚本块体的文本，功能块或scriptlet。|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|返回标识一 `IScriptEntry` 对象的项目名称。|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|为表示单个对象的项\(如函数\)，返回对象的名称。|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|返回项的起始位置和长度。|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|返回 `IScriptEntry` 函数对象的类型信息。|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|返回对应于 `IScriptEntry` 脚本块或源代码。`IScriptScriptlet` 事件处理程序中包含的文本。|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|将 `IScriptEntry` 脚本块体的文本或 `IScriptScriptlet` scriptlet。|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|设置标识一 `IScriptEntry` 对象的项目名称。|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|为表示单个对象的项\(如函数\)，设置对象的名称。|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|设置 `IScriptEntry` 函数对象的类型信息。|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|设置对应于 `IScriptEntry` 脚本块或源代码。`IScriptScriptlet` 事件处理程序中包含的文本。|  
  
## 请参阅  
 [活动脚本创作接口](../../winscript/reference/active-script-authoring-interfaces.md)