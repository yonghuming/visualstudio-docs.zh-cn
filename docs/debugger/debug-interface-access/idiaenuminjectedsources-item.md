---
title: "Idiaenuminjectedsources:: Item |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b53112756a35c190668e76ba3bb1114ec60eb85
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
通过索引中检索插入的源。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### <a name="parameters"></a>参数  
 索引  
 [in]索引的[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)要检索的对象。 索引是范围为 0 到`count`-1，其中`count`返回[idiaenuminjectedsources:: Get_count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)方法。  
  
 injectedSource  
 [out]返回[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)表示插入的源对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)