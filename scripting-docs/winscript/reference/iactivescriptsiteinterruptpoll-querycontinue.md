---
title: "IActiveScriptSiteInterruptPoll::QueryContinue |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteInterruptPoll.QueryContinue
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93323d500ae7e99957c365d60741fa612ba0fc34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
允许主机可以指定脚本应终止。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>参数  
 此方法采用任何参数。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|调用成功，且主机允许脚本继续运行。|  
|`S_FALSE`|成功的调用和脚本终止主机请求。|  
  
## <a name="remarks"></a>备注  
 托管的脚本应终止除非的返回值`QueryContinue`方法是`S_OK`。 返回值`S_FALSE`指示主机显式请求脚本终止。  
  
 可以使用多线程的主机`IActiveScript::InterruptScriptThread`方法终止脚本。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSiteInterruptPoll 接口](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)