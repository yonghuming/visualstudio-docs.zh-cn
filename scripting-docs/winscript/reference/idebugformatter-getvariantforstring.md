---
title: "IDebugFormatter::GetVariantForString |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugFormatter.GetVariantForString
apilocation: jscript.dll
helpviewer_keywords: IDebugFormatter::GetVariantForString
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f9f783c8fe1864999e017ff348853df5464c93f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
返回包含给定的字符串的变量。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pwstrValue`  
 [in]要在一个变量中存储的字符串。  
  
 `pvar`  
 [out]VARIANT 包含`pwstrValue`。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法返回包含给定的字符串的变量。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugFormatter 接口](../../winscript/reference/idebugformatter-interface.md)