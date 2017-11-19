---
title: "IScriptEntry::GetBody |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetBody
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9daa04009cf7088cbd21a2d3dfa185f581c157a3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
返回的正文对应的文本`IScriptEntry`脚本块、 函数块或 scriptlet。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pbstr`  
 [out]在以下一项的正文中的文本：  
  
-   `IScriptEntry`脚本块  
  
-   `IScriptEntry`函数块中的函数  
  
-   `IScriptEntry` Scriptlet 事件处理程序  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)