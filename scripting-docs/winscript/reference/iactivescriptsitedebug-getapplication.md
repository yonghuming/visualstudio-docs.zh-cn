---
title: "IActiveScriptSiteDebug::GetApplication |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteDebug.GetApplication
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteDebug::GetApplication
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e33bf254d2e688451f1b69a3b3eb1b676a9e9b1a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebuggetapplication"></a>IActiveScriptSiteDebug::GetApplication
返回与此脚本站点关联的调试应用程序对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppda`  
 [out]与脚本站点关联的调试应用程序对象的指针。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|主机不直接支持调试。|  
  
## <a name="remarks"></a>备注  
 `GetApplication`方法为提供的方法来定义每个脚本所属的应用程序对象的智能主机。 脚本引擎应尝试调用此方法以获取其包含的应用程序，并采用`IProcessDebugManager::GetDefaultApplication`如果此操作失败。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSiteDebug 接口](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)