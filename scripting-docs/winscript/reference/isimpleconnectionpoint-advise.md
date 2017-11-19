---
title: "ISimpleConnectionPoint::Advise |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISimpleConnectionPoint.Advise
apilocation: pdm.dll
helpviewer_keywords: ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ec43d135401386a3f54f2c047040897f038ba19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
建立简单的连接点对象和客户端的接收器之间的连接。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdisp`  
 [in]指向`IDispatch`客户端上的接口的建议接收器。 客户端的接收器接收从简单的连接点的传出调用。  
  
 `pdwCookie`  
 [out]指向返回的令牌，用于唯一标识此连接。 调用方在更高版本使用此标记可将其传递给删除连接`ISimpleConnectionPoint::Unadvise`方法。 如果未成功建立连接，则此值为零。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法建立简单的连接点对象和客户端的接收器之间的连接。  
  
## <a name="see-also"></a>另请参阅  
 [ISimpleConnectionPoint 接口](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)