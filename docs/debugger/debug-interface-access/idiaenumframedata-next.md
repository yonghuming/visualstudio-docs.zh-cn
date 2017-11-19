---
title: "Idiaenumframedata:: Next |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ef6ba1cb860a1346db794e47a76258f80d57707
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
检索指定的数目的帧枚举序列中的数据元素。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### <a name="parameters"></a>参数  
 celt  
 [in]要检索的枚举器中的帧数据元素的数目。  
  
 rgelt  
 [out]数组[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)要使用的请求的框架数据元素填充的对象。  
  
 pceltFetched  
 [out]在提取枚举器返回帧数据元素的数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`。 返回`S_FALSE`如果没有更多记录。 否则，返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)