---
title: "IActiveScript::SetScriptState |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.SetScriptState
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 146cd5e4f2b6137fc6fe6e32e8ca153c3aab8fd5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
将脚本引擎的给定状态。 此方法可以从非基本线程调用不会导致为主机对象或设置为非基本标注[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)接口。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ss`  
 [in]将脚本引擎设置为给定状态。 可以是中定义的值之一[SCRIPTSTATE 枚举](../../winscript/reference/scriptstate-enumeration.md)枚举。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_FAIL`|脚本引擎不支持恢复到初始化状态的转换。 主机必须放弃此脚本引擎和创建、 初始化和加载一个新的脚本引擎来实现相同的效果。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎具有尚未加载或初始化），因此失败。|  
|`OLESCRIPT_S_PENDING`|此方法已排队成功，但尚未未更改状态。 当状态更改，站点将被回叫通过[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法。|  
|`S_FALSE`|方法成功，但该脚本已处于给定状态。|  
  
## <a name="remarks"></a>备注  
 有关脚本引擎状态的详细信息，请参阅的脚本引擎状态部分[Windows 脚本引擎](../../winscript/windows-script-engines.md)。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)