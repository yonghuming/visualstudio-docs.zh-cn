---
title: "Idiaenumtables:: Item |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26acf7b8f9ad54a1ef1ed25497cd408c51c745c5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
检索通过索引或名称的表。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>参数  
 `index`  
 [in]索引或名称[IDiaTable](../../debugger/debug-interface-access/idiatable.md)要检索。 如果使用整数变体，则它必须是范围 0 到`count`-1，其中`count`是通过返回[idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)方法。  
  
 `table`  
 [out]返回[IDiaTable](../../debugger/debug-interface-access/idiatable.md)表示所需的表对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 如果指定一个字符串变量，则该字符串命名特定表。 中定义的名称应表名称之一[常量 (调试接口访问 SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)。  
  
## <a name="example"></a>示例  
  
```C++  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>另请参阅  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [常量（调试接口访问 SDK）](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)