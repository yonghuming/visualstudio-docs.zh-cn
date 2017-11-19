---
title: "Idiasymbol:: Get_registerid |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5fe8b131e715f5fa55d2d2f99cb8c4714996290
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
检索的位置的注册指示符时[LocationType 枚举](../../debugger/debug-interface-access/locationtype.md)设置为`LocIsEnregistered`。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pRetVal`  
 [out]返回的位置的注册指示符。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回`S_FALSE`或错误代码。  
  
> [!NOTE]
>  返回值`S_FALSE`意味着属性不是可用于符号。  
  
## <a name="remarks"></a>备注  
 如果符号是相对于寄存器，即如果符号的[LocationType 枚举](../../debugger/debug-interface-access/locationtype.md)设置为`LocIsRegRel`，使用`get_registerId`方法接着调用[idiasymbol:: Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)若要获取的偏移量从符号所在的位置的寄存器的方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 枚举](../../debugger/debug-interface-access/locationtype.md)