---
title: "活动脚本常量、枚举和错误代码 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# 活动脚本常量、枚举和错误代码
本节描述用于Windows和错误代码的枚举脚本引擎。  
  
## 常量  
  
|常量|说明|  
|--------|--------|  
|[SCRIPTTHREADID 常量](../../winscript/reference/scriptthreadid-constants.md)|指定线程的类型。|  
  
## 属性  
  
|属性|说明|  
|--------|--------|  
|[SCRIPTPROP\_HOSTKEEPALIVE 属性](../../winscript/reference/scriptprop-hostkeepalive-property.md)|用于指定是否应保持脚本引擎完整功能，如果具有未处理的引用。|  
  
## 枚举  
  
|Enumeration|说明|  
|-----------------|--------|  
|[SCRIPTGCTYPE 枚举](../../winscript/reference/scriptgctype-enumeration.md)|垃圾回收的类型执行的。|  
|[SCRIPTLANGUAGEVERSION 枚举](../../winscript/reference/scriptlanguageversion-enumeration.md)|指定可的脚本版本。|  
|[SCRIPTSTATE 枚举](../../winscript/reference/scriptstate-enumeration.md)|指定一个脚本引擎的状态。|  
|||  
|[SCRIPTTHREADSTATE 枚举](../../winscript/reference/scriptthreadstate-enumeration.md)|在一个脚本引擎指定线程的状态。|  
|[SCRIPTTRACEINFO 枚举](../../winscript/reference/scripttraceinfo-enumeration.md)|表示要跟踪的脚本事件。  使用在 [IActiveScriptSiteTraceInfo::SendScriptTraceInfo 方法](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)。|  
|[SCRIPTUICHANDLING 枚举](../../winscript/reference/scriptuichandling-enumeration.md)|表示应接近于控件的方法。|  
|[SCRIPTUICITEM 枚举](../../winscript/reference/scriptuicitem-enumeration.md)|表示UI项类型。  使用在 [IActiveScriptSiteUIControl::GetUIBehavior 方法](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)。|  
  
## 错误代码  
  
|错误代码|说明|  
|----------|--------|  
|[SCRIPT\_E\_PROPAGATE 错误代码](../../winscript/reference/script-e-propagate-error-code.md)|脚本错误传播给调用方，可能是在不同的线程。|  
|[SCRIPT\_E\_RECORDED 错误代码](../../winscript/reference/script-e-recorded-error-code.md)|错误已通过在脚本引擎和宿主之间。|  
|[SCRIPT\_E\_REPORTED 错误代码](../../winscript/reference/script-e-reported-error-code.md)|脚本引擎未经处理的异常移到宿主报告。|  
  
## 请参阅  
 [活动脚本接口](../../winscript/reference/active-script-interfaces.md)