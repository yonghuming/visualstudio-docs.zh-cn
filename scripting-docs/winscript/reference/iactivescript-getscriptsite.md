---
title: "IActiveScript::GetScriptSite |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 961483d45c72018bc216306d6c1aba0400a367ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
检索与 Windows 脚本引擎关联的站点对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>参数  
 `iid`  
 [in]所请求的接口的标识符。  
  
 `ppvSiteObject`  
 [out]接收到主机的站点对象的接口指针的位置的地址。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|自变量无效。|  
|`E_NOINTERFACE`|不支持指定的接口。|  
|`E_POINTER`|指定了无效的指针。|  
|`S_FALSE`|没有站点的设置;`ppvSiteObject`参数设置为`NULL`。|  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)