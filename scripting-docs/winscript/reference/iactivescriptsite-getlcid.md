---
title: "IActiveScriptSite::GetLCID |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6e128f5ac5de11b45af59c83750411c35e6efa7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
检索与主机的用户界面关联的区域设置标识符。 脚本引擎使用标识符来确保，错误字符串和引擎生成的其他用户界面元素出现在适当的语言。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>参数  
 `plcid`  
 [out]接收显示通过脚本引擎的用户界面元素的区域设置标识符的变量的地址。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|未实现此方法。 使用系统定义的区域设置。|  
|`E_POINTER`|指定了无效的指针。|  
  
## <a name="remarks"></a>备注  
 如果此方法返回`E_NOTIMPL`，应使用系统定义的区域设置标识符。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)