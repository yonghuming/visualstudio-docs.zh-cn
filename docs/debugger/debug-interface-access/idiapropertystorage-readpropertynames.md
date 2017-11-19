---
title: "IDiaPropertyStorage::ReadPropertyNames |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 338d2c4f59eb9023d8a7d8c8618585bb902785f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
检索对应的字符串名称给定属性标识符。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>参数  
 `cpropid`  
 [in]中的属性 id 数`rgpropid`。  
  
 `rgpropid`  
 [in]要为其获取名称的属性 id 的数组 (`PROPID`作为 WTypes.h 中定义`ULONG`)。  
  
 `rglpwstrName`  
 [在中，out]指定的属性 id 的属性名称的数组。 该数组必须是预分配，以容纳的属性名称请求的数，并且必须能够以容纳至少`cpropid``BSTR`字符串。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则返回错误代码。  
  
## <a name="remarks"></a>备注  
 返回的属性名称必须被释放 (通过调用`SysFreeString`函数) 它们不再需要时。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)