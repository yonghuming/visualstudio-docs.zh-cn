---
title: "IActiveScriptSite::OnLeaveScript |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnLeaveScript
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba20c13dc5568165641c5c7b8e871e0b5e8f322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
通知主机脚本引擎已返回从执行脚本代码。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 `S_OK`。  
  
## <a name="remarks"></a>备注  
 脚本引擎必须将控制返回到调用应用程序中，输入脚本引擎之前调用此方法。 例如，如果该脚本调用一个对象，然后触发通过脚本引擎来处理事件时，脚本引擎必须调用[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)方法，然后才能执行该事件，并必须调用`IActiveScriptSite::OnLeaveScript`后返回到即触发事件的对象之前执行该事件。 可以嵌套调用此方法。 对每个调用`IActiveScriptSite::OnEnterScript`需要相应地调用此方法。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)