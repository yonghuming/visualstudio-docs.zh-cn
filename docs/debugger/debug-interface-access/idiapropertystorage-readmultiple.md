---
title: "IDiaPropertyStorage::ReadMultiple |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77ead9e28f86067c08aa610fc902f2a0847bfb25
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
读取指定从当前的属性集的属性。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>参数  
 `cpspec`  
 [in]属性中指定的计数`rgpspec`数组。 如果为零，该方法返回没有属性，但返回`S_OK`作为成功代码。  
  
 `rgpspec`  
 [in]要读取的属性数组。 属性 ID 或可选的字符串名称，可以指定属性。 不需要在数组中的任何特定顺序指定属性。 该数组可以包含重复的属性，从而导致重复的属性上的简单属性的返回的值。 非简单属性应返回尝试打开它们第二次拒绝访问。 该数组可以包含混合的属性 Id 和字符串 Id。 此数组必须至少具有`cpspec`数属性值。  
  
 `rgvar`  
 [在中，out]数组`PROPVARIANT`结构 （Microsoft.VisualStudio.OLE.Interop 命名空间中） 以使用每个属性的值进行填充。 该数组必须至少是`cpspec`大小中的元素。 调用方不需要初始化数组中的值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`。 返回`S_FALSE`如果未找到一个或多个属性。 否则返回错误代码。  
  
## <a name="remarks"></a>备注  
 如果未找到属性，对应项`rgvar`数组包含`VARIANT`类型为`VT_EMPTY`。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)