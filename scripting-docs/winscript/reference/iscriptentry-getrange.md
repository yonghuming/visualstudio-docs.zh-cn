---
title: "IScriptEntry::GetRange |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetRange
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ae0ee34298e03fdd2e9c6bc841d9fbe90967e8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
返回的起始位置和长度的一个条目。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pichMin`  
 [out]有关`IScriptEntry`指定脚本块的对象，则返回 0。  
  
 有关`IScriptEntry`指定是函数对象，对象在当前脚本块中返回该函数的开始位置。  
  
 有关`IScriptScriptlet`对象，则返回 0。  
  
 `pcch`  
 [out]有关`IScriptEntry`指定脚本块中，对象返回文本的长度。  
  
 有关`IScriptEntry`指定一个函数对象的对象返回的函数定义长度。  
  
 有关`IScriptScriptlet`对象，则返回的项的长度。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)