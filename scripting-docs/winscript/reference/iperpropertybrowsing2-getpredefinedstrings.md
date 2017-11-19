---
title: "IPerPropertyBrowsing2::GetPredefinedStrings |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IPerPropertyBrowsing2.GetPredefinedStrings
apilocation: scrobj.dll
helpviewer_keywords: IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e07d52eca9434acc7e54f3b35b111cf12af0a871
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
允许调用方使用的字符串指针表示此属性的可能值的计数数组填充列表框。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dispid`  
 [in]为其调用方请求的字符串列表的属性的调度标识符。  
  
 `pCaStrings`  
 [out]指向包含的元素计数和地址方法分配的字符串指针数组的调用方分配的计数数组结构的指针。 如果此方法失败，会分配任何内存，并是不确定的结构的内容。  
  
 `pCaCookies`  
 [out]指向包含的元素计数和地址方法分配的 dword 值数组的调用方分配的计数数组结构的指针。 如果此方法失败，会分配任何内存，并是不确定的结构的内容。  
  
## <a name="return-value"></a>返回值  
 返回一个有效`HRESULT`，通常`S_OK`。  
  
## <a name="see-also"></a>另请参阅  
 [IPerPropertyBrowsing2 接口 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)