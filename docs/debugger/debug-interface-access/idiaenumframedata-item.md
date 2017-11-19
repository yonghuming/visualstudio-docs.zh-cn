---
title: "Idiaenumframedata:: Item |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a33a0dad9f315f929a2ca0b032f8907f9567435b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
通过索引中检索框架数据元素。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>参数  
 索引  
 [in]索引的[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)要检索的对象。 索引是范围 0 到`count`-1，其中`count`返回[idiaenumframedata:: Get_count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)方法。  
  
 section  
 [out]返回[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)对象，表示所需的框架数据元素。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)