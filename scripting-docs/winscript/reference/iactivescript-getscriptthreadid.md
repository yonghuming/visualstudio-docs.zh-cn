---
title: "IActiveScript::GetScriptThreadID |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8850319035b7b5e3a9cbbd4bbe4340e1eefacc96
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
检索与给定的 Win32 线程关联的线程的脚本引擎定义标识符。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwWin32ThreadID` ,  
 [in]当前进程中正在运行的 Win32 线程的线程标识符。 使用[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)函数可检索当前正在执行的线程的线程标识符。  
  
 `pstidThread` ,  
 [out]接收与给定的 Win32 线程关联的脚本线程标识符的变量的地址。 此标识符的解释为从左到脚本引擎中，但它可以是只是一份 Windows 线程标识符。 请注意，是否 Win32 线程终止，则此标识符将为未分配并且随后可以分配给另一个线程。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_POINTER`|指定了无效的指针。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎具有尚未加载或初始化），因此失败。|  
  
## <a name="remarks"></a>备注  
 检索到的标识符可以如到脚本线程执行控制方法的后续调用中使用[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)方法。  
  
 此方法可以从非基本线程调用不会导致为主机对象或设置为非基本标注[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)接口。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)