---
title: "Idiaenumsymbols:: Clone |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSymbols::Clone method
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9409541a0784479cc466accc9b9184ba5f220196
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
创建包含与当前的枚举器相同的枚举状态的枚举。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT Clone (   
   IDiaEnumSymbols** ppenum  
);  
```  
  
#### <a name="parameters"></a>参数  
 ppenum  
 [out]返回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)对象，其中包含重复的枚举数。 不重复符号，仅枚举数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)