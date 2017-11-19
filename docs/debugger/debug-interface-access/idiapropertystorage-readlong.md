---
title: "IDiaPropertyStorage::ReadLONG |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba26ae4e2495d8c0a4feb1ff692d90a228e8292
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
读取`LONG`属性组中的值。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>参数  
 `id`  
 [in]要读取的属性的标识符 (`PROPID`作为 WTypes.h 中定义`ULONG`)。  
  
 `pValue`  
 [out]返回属性值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则返回错误代码。 返回`E_INVALIDARG`如果属性的类型不是`LONG`。  
  
## <a name="remarks"></a>备注  
 A`LONG`由 Windows 作为 32 位有符号整数。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)