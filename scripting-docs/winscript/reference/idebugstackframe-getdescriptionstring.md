---
title: "IDebugStackFrame::GetDescriptionString |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrame.GetDescriptionString
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrame::GetDescriptionString
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cdc77aa2ef2f9d7c95b0b82d5195a6a73524f055
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
返回的堆栈帧的短或长文本说明。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>参数  
 `fLong`  
 [in]标志，其中`TRUE`返回较长的说明和`FALSE`返回的简短说明。  
  
 `pbstrDescription`  
 [out]堆栈帧的说明。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 通常情况下，如果`fLong`是`FALSE`，此方法提供仅与堆栈帧关联的函数的名称。 当`fLong`是`TRUE`，此方法可能还提供的函数参数和其他相关信息。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugStackFrame 接口](../../winscript/reference/idebugstackframe-interface.md)