---
title: "SCRIPTTHREADID 常量 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SCRIPTTHREADID
apilocation: scrobj.dll
helpviewer_keywords: SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc692716115ea0c205b1cfd982b189fffd54a9ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID 常量
用于指定线程的类型。  
  
## <a name="syntax"></a>语法  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>常量  
  
|常量|值|含义|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|当前正在执行的线程。|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|基线程;也就是说，在其中的脚本引擎的线程已实例化。|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|所有线程。|  
  
## <a name="remarks"></a>备注  
 `SCRIPTTHREADID`类型由`IActiveScript::GetCurrentScriptThreadID`， `IActiveScript::GetScriptThreadID`， `IActiveScript::GetScriptThreadState`，和`IActiveScript::InterruptScriptThread`，但常量仅可以由`IActiveScript::GetScriptThreadState`和`IActiveScript::InterruptScriptThread`。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)