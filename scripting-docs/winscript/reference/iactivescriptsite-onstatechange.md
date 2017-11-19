---
title: "IActiveScriptSite::OnStateChange |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnStateChange
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnStateChange
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fae7782d713ab226e57e687cda8eb4ccdb54cf20
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonstatechange"></a>IActiveScriptSite::OnStateChange
通知主机脚本引擎已更改状态。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ssScriptState`  
 [in]值，该值指示新的脚本状态。 请参阅[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)方法有关的状态的说明。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 `S_OK`。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)