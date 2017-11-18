---
title: "IActiveScriptError::GetSourcePosition |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptError.GetSourcePosition
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d63310a8ba5cfda39d48a482eaf7c345cd492adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
检索错误发生时脚本引擎已运行脚本的源代码中的位置。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdwSourceContext`  
 [out]接收标识上下文 cookie 变量的地址。 此参数的解释取决于宿主应用程序。  
  
 `pulLineNumber`  
 [out]在发生错误的源文件中接收的行号的变量的地址。  
  
 `pichCharPosition`  
 [out]一个变量来接收发生错误的行中的字符位置的地址。  
  
## <a name="return-value"></a>返回值  
 返回`S_OK`如果成功，或`E_FAIL`如果检索不到位置。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)