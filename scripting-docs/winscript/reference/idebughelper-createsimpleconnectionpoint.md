---
title: "IDebugHelper::CreateSimpleConnectionPoint |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugHelper.CreateSimpleConnectionPoint
apilocation: pdm.dll
helpviewer_keywords: IDebugHelper::CreateSimpleConnectionPoint
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcc598fa97d47a564ddb12aaa0480e42b6601118
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelpercreatesimpleconnectionpoint"></a>IDebugHelper::CreateSimpleConnectionPoint
返回一个事件的接口，用于包装给定`IDispatch`对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp  
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdisp`  
 [in]`IDispatch`对象包装。  
  
 `ppscp`  
 [out]包装的事件接口`pdisp`。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 返回一个事件的接口，用于包装给定`IDispatch`(请参阅[ISimpleConnectionPoint 接口](../../winscript/reference/isimpleconnectionpoint-interface.md))。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugHelper 接口](../../winscript/reference/idebughelper-interface.md)   
 [ISimpleConnectionPoint 接口](../../winscript/reference/isimpleconnectionpoint-interface.md)