---
title: "IActiveScriptSite |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c23dba403a7889fe46817a21ed8e4be65b1c05b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
由主机后，可以创建一个网站，用于 Windows 脚本引擎实现。 通常情况下，此站点将与所有对象都可见的脚本 （例如，ActiveX 控件） 的容器相关联。 通常情况下，此容器将对应于文档或正在查看的页面。 例如，Microsoft Internet Explorer 中，将创建此类容器正在显示每个 HTML 页面。 每个 ActiveX 控件 （或其他自动化对象） 上的网页和脚本引擎本身，将为此容器中的可枚举。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|||  
|-|-|  
|方法|描述|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|检索由主机使用用于显示用户界面元素的区域设置标识符。|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|获取有关已添加到引擎通过调用某个项的信息[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法。|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|检索唯一标识当前的文档版本从主机的角度来看是主机定义的字符串。|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|当脚本已完成执行时调用。|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|通知主机脚本引擎已更改状态。|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|通知主机引擎运行脚本时发生了执行错误。|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|通知主机脚本引擎已开始执行脚本代码。|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|通知主机脚本引擎已返回从执行脚本代码。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本接口](../../winscript/reference/active-script-interfaces.md)