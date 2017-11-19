---
title: "IActiveScript::GetCurrentScriptThreadID |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5921dc4d0f9a9bf0d505fece0f47354cb16d440c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
检索当前正在执行的线程的脚本引擎定义标识符。 标识符可以如脚本线程执行控制方法的后续调用中使用[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)方法。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstidThread`  
 [out]接收与当前线程关联的脚本线程标识符的变量的地址。 此标识符的解释为从左到脚本引擎中，但它可以是只是一份 Windows 线程标识符。 如果 Win32 线程终止，此标识符将为未分配，并且随后可以分配给另一个线程。  
  
## <a name="return-value"></a>返回值  
 返回`S_OK`如果成功，或`E_POINTER`如果指定了无效的指针。  
  
## <a name="remarks"></a>备注  
 此方法可以从非基本线程调用不会导致为主机对象或设置为非基本标注[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)接口。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)