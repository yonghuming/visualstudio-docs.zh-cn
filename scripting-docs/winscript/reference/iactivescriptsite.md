---
title: "IActiveScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSite 接口"
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite
实现由宿主创建Windows脚本引擎的站点。  通常，此站点将与例如是可见的。该脚本的容器所有对象\(，ActiveX控件\)。  通常，此容器将对应于文档或调用中查看。  Microsoft Internet Explorer，例如，将创建显示的每个HTML页这样的一个容器。  每个ActiveX控件\(或其他自动化对象\)在页和脚本引擎，此容器内是可枚举的。  
  
## Vtable 顺序中的方法  
  
|||  
|-|-|  
|方法|说明|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|检索宿主用于显示用户界面元素使用的区域设置标识符。|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|获取有关添加到一个引擎传递给 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 方法的调用的信息。|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|检索唯一标识当前文件版本从宿主视图的主机中定义的字符串。|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|调用，当脚本完成执行。|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|通知宿主脚本引擎更改状态。|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|通知宿主实现发生错误，当引擎运行该脚本时。|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|通知宿主脚本引擎开始执行脚本代码。|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|通知宿主脚本引擎通过执行脚本代码返回。|  
  
## 请参阅  
 [活动脚本接口](../../winscript/reference/active-script-interfaces.md)