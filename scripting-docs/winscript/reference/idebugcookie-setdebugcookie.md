---
title: "IDebugCookie::SetDebugCookie |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugCookie.SetDebugCookie
apilocation: pdm.dll
helpviewer_keywords: IDebugCookie::SetDebugCookie
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1155b00750cfe2a91625ba0f531622f381467198
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugcookiesetdebugcookie"></a>IDebugCookie::SetDebugCookie
设置调试应用程序 cookie。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwDebugAppCookie`  
 [in]一个标识的调试应用程序的 cookie。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法会设置该调试应用程序 cookie，允许多个调试器附加到进程。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugCookie 接口](../../winscript/reference/idebugcookie-interface.md)