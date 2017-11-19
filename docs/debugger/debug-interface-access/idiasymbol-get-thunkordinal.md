---
title: "Idiasymbol:: Get_thunkordinal |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9eb23f90ea960f927ab8561ff215968134bc30e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
检索函数的转换 （thunk） 类型。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pRetVal`  
 [out]返回一个值从[THUNK_ORDINAL 枚举](../../debugger/debug-interface-access/thunk-ordinal.md)指定函数的转换 （thunk） 类型的枚举。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回`S_FALSE`或错误代码。  
  
> [!NOTE]
>  返回值`S_FALSE`意味着属性不是可用于符号。  
  
## <a name="remarks"></a>备注  
 此属性才有效才形式的符号[SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)值`SymTagThunk`。  
  
 "转换 （thunk）"是代码的一种 32 位内存地址空间 （也称为平面地址空间） 和 （称为分段的地址空间） 的 16 位地址空间之间进行转换。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK_ORDINAL 枚举](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)