---
title: "IActiveScriptSite::OnScriptTerminate |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnScriptTerminate
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eef8bd2a3f2e2a4eb4fd4b5f0e35fcd9acfe5bc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
通知主机脚本已完成执行。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pvarResult`  
 [in]包含脚本的结果，将变量的地址或`NULL`如果脚本不生成任何结果。  
  
 `pexcepinfo`  
 [in]地址`EXCEPINFO`包含时脚本终止，生成的异常信息的结构或`NULL`如果不生成异常。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 `S_OK`。  
  
## <a name="remarks"></a>备注  
 脚本引擎调用此方法对的调用之前[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法，设置了 SCRIPTSTATE_INITIALIZED 标志完成。 可以使用此方法以返回到主机的完成状态和结果。 请注意，许多的脚本语言，基于从主机中接收事件，具有由主机定义的有效期。 在这种情况下，可能永远不会调用此方法。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)