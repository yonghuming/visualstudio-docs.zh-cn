---
title: "IScriptNode::Delete |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.Delete
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d1404d90cc1edd882505e463938a2c1a5e8aea8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
删除此对象树。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>参数  
 该方法采用任何参数。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 后`Delete`调用方法时， [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)方法应指明该脚本节点处于不活动状态。  
  
## <a name="see-also"></a>另请参阅  
 [IScriptNode 接口](../../winscript/reference/iscriptnode-interface.md)