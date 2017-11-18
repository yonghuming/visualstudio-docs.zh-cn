---
title: "IActiveScript::SetScriptSite |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11fa9003abb03c42adcbf3a548bb5b90d763a344
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
通知的脚本引擎[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)主机提供的接口站点。 调用此方法之前任何其他[IActiveScript](../../winscript/reference/iactivescript.md)使用接口方法。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pScriptSite`  
 [in]要与脚本引擎的此实例相关联的主机提供的脚本站点的地址。 站点必须唯一地分配给此脚本的引擎实例;它不能与其他脚本引擎中共享。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_FAIL`|出现未知的错误;脚本引擎无法完成初始化站点。|  
|`E_INVALIDARG`|自变量无效。|  
|`E_POINTER`|指定了无效的指针。|  
|`E_UNEXPECTED`|不应调用 （例如，已设置站点）。|  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)