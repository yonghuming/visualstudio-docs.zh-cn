---
title: "SCRIPTSTATE 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e062a9c2f3076144063ffb77895c8a03ecc4ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE 枚举
指定的脚本引擎的状态。 此枚举由[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) ， [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) ，和[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>枚举值  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|脚本刚刚创建，但尚未尚未初始化使用`IPersist*`接口和[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) 。|  
|SCRIPTSTATE_INITIALIZED|脚本已初始化，但未运行 （连接到其他对象或接收事件） 或执行任何代码。 代码可以通过调用查询的执行[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)方法。|  
|SCRIPTSTATE_STARTED|脚本可以执行代码，但尚未不接收添加的对象的事件[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法。|  
|SCRIPTSTATE_CONNECTED|加载脚本，并将其连接以接收事件。|  
|SCRIPTSTATE_DISCONNECTED|脚本加载和运行时执行状态，但暂时断开接收事件。|  
|SCRIPTSTATE_CLOSED|脚本已关闭。 脚本引擎不再运行，并不再针对多数方法返回错误。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本常量、枚举和错误代码](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)