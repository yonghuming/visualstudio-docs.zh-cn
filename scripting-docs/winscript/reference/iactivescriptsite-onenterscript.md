---
title: "IActiveScriptSite::OnEnterScript |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnEnterScript
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb4514770faaaad46c8590e6df03488e3d5bc679
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
通知主机脚本引擎已开始执行脚本代码。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 `S_OK`。  
  
## <a name="remarks"></a>备注  
 到脚本引擎，脚本引擎必须在每个条目或重入调用此方法。 例如，如果该脚本调用一个对象，然后触发通过脚本引擎来处理事件时，脚本引擎必须调用`IActiveScriptSite::OnEnterScript`之前执行该事件，并必须调用[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)方法执行事件之后、 之前返回到即触发事件的对象。 可以嵌套调用此方法。 每次调用此方法需要相应地调用`IActiveScriptSite::OnLeaveScript`。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)