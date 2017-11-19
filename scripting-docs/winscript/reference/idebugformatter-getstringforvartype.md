---
title: "IDebugFormatter::GetStringForVarType |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugFormatter.GetStringForVarType
apilocation: jscript.dll
helpviewer_keywords: IDebugFormatter::GetStringForVarType
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e056fa2ef9613c1af776840d1dae61078e26f83
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformattergetstringforvartype"></a>IDebugFormatter::GetStringForVarType
返回表示给定的 VARTYPE 值的字符串。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `vt`  
 [in]VARTYPE 无法表示为一个字符串。  
  
 `ptdescArrayType`  
 [in]描述类型的结构数组。  
  
 `pbstr`  
 [out]字符串表示`vt`。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 该方法返回表示给定的 VARTYPE 值的字符串。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugFormatter 接口](../../winscript/reference/idebugformatter-interface.md)