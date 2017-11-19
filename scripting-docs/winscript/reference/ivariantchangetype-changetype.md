---
title: "IVariantChangeType::ChangeType |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d742d1bd57c85aa75c9ccd60479d08c1a559fb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
可将变量值并创建具有指定类型的新变量。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pvarDst`  
 [在中，out]一个变量，包含表示的值`pvarSrc`，但与由指定类型`vtNew`。  
  
 `pvarSrc`  
 [in]要将更改为新类型的变量值。  
  
 `lcid`  
 [in]要将参数转换到数据库或从字符串时使用的区域设置上下文。  
  
 `vtNew`  
 [in]指定的类型`pvarDst`成为。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 `pvarDst`和`pvarSrc`参数可以为相等，这种情况下覆盖原始值。 此方法将传递`pvarDst`到`VariantClear`函数，并因此`pvarDst`应初始化为有效的值。  
  
## <a name="see-also"></a>另请参阅  
 [IVariantChangeType 接口](../../winscript/reference/ivariantchangetype-interface.md)