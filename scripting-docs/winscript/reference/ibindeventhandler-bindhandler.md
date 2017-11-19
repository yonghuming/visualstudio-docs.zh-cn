---
title: "IBindEventHandler::BindHandler |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IBindEventHandler.BindHandler
apilocation: scrobj.dll
helpviewer_keywords: IBindEventHandler::BindHandler
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66de7cba8181ce9f3d683a90e4d7dd51e63d4779
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ibindeventhandlerbindhandler"></a>IBindEventHandler::BindHandler
将事件绑定到对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrEvent`  
 [in]指定要处理的事件。  
  
 `pdisp`  
 [in]指定要处理该事件的对象。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法将事件绑定到对象。  
  
## <a name="see-also"></a>另请参阅  
 [IBindEventHandler 接口](../../winscript/reference/ibindeventhandler-interface.md)