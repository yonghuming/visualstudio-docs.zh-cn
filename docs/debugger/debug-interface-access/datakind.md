---
title: "DataKind |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e9ffa36facb3c7f64f7eb2c0b96ef5209f70c78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="datakind"></a>DataKind
指示数据值的特定范围。  
  
## <a name="syntax"></a>语法  
  
```C++  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>元素  
 DataIsUnknown  
 无法确定 data 符号。  
  
 DataIsLocal  
 数据项是一个本地变量。  
  
 DataIsStaticLocal  
 数据项是静态局部变量。  
  
 DataIsParam  
 数据项是正式参数。  
  
 DataIsObjectPtr  
 数据项是一个对象指针 (`this`)。  
  
 DataIsFileStatic  
 数据项是文件范围内的变量。  
  
 DataIsGlobal  
 数据项是全局变量。  
  
 DataIsMember  
 数据项是一个对象成员变量。  
  
 DataIsStaticMember  
 数据项是类的静态变量。  
  
 DataIsConstant  
 数据项是一个常量值。  
  
## <a name="remarks"></a>备注  
 此枚举中的值由[idiasymbol:: Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)方法。  
  
## <a name="requirements"></a>要求  
 标头： cvconst.h  
  
## <a name="see-also"></a>另请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)