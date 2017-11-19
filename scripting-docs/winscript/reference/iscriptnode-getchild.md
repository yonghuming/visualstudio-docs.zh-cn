---
title: "IScriptNode::GetChild |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.GetChild
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d127b1b8a8db0c6d272e50d33b523fbe182a9e21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
返回位于指定索引的节点中的子级。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>参数  
 `isn`  
 [in]父代中的子级的索引。  
  
 `ppsn`  
 [out]接收指向的变量的地址`IScriptNode`接口的子实例。  
  
 有关`IScriptNode`表示网页上的对象，此参数将返回一个对象，包含脚本块。  
  
 有关`IScriptEntry`指定脚本块的对象，此参数返回指定的函数的对象。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 有关`IScriptEntry`指定的函数对象的对象和`IScriptScriptlet`对象，此方法失败，因为不存在子条目。  
  
## <a name="see-also"></a>另请参阅  
 [IScriptNode 接口](../../winscript/reference/iscriptnode-interface.md)