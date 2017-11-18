---
title: "活动脚本常量、 枚举和错误代码 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb4165a5471c8e79827f0f7605cef575e82bab75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>活动脚本常量、枚举和错误代码
本部分介绍的枚举和使用在 Windows 脚本引擎中的错误代码。  
  
## <a name="constants"></a>常量  
  
|常量|描述|  
|--------------|-----------------|  
|[SCRIPTTHREADID 常量](../../winscript/reference/scriptthreadid-constants.md)|指定的线程的类型。|  
  
## <a name="properties"></a>属性  
  
|属性|描述|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE 属性](../../winscript/reference/scriptprop-hostkeepalive-property.md)|用于指定应保持脚本引擎完全正常运行，如果有未处理引用。|  
  
## <a name="enumerations"></a>枚举  
  
|枚举|描述|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE 枚举](../../winscript/reference/scriptgctype-enumeration.md)|若要执行的垃圾回收的类型。|  
|[SCRIPTLANGUAGEVERSION 枚举](../../winscript/reference/scriptlanguageversion-enumeration.md)|指定脚本版本的可能。|  
|[SCRIPTSTATE 枚举](../../winscript/reference/scriptstate-enumeration.md)|指定的脚本引擎的状态。|  
|||  
|[SCRIPTTHREADSTATE 枚举](../../winscript/reference/scriptthreadstate-enumeration.md)|指定脚本引擎中的线程的状态。|  
|[SCRIPTTRACEINFO 枚举](../../winscript/reference/scripttraceinfo-enumeration.md)|表示正在跟踪的脚本事件。 在中使用[iactivescriptsitetraceinfo:: Sendscripttraceinfo 方法](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)。|  
|[SCRIPTUICHANDLING 枚举](../../winscript/reference/scriptuichandling-enumeration.md)|表示应处理 UI 控件的方式。|  
|[SCRIPTUICITEM 枚举](../../winscript/reference/scriptuicitem-enumeration.md)|表示 UI 项的类型。 在中使用[iactivescriptsiteuicontrol:: Getuibehavior 方法](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)。|  
  
## <a name="error-codes"></a>错误代码  
  
|错误代码|描述|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE 错误代码](../../winscript/reference/script-e-propagate-error-code.md)|脚本错误被传播到调用方，这可能是在不同线程中。|  
|[SCRIPT_E_RECORDED 错误代码](../../winscript/reference/script-e-recorded-error-code.md)|脚本引擎和主机之间传递了错误。|  
|[SCRIPT_E_REPORTED 错误代码](../../winscript/reference/script-e-reported-error-code.md)|脚本引擎已报告到的主机未处理的异常。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本接口](../../winscript/reference/active-script-interfaces.md)