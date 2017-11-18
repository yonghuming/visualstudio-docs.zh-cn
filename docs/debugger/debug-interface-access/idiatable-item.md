---
title: "Idiatable:: Item |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5c0c810dfd1a17f2fa63e64bf199a5882174aae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiatableitem"></a>IDiaTable::Item
检索表中指定的项的引用。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>参数  
 `index`  
 [in]范围在 0 到的表项的索引`count`-1，其中`count`返回[idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)方法。  
  
 `element`  
 [out]返回`IUnknown`表示的指定的表项的对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 表表示的对象的集合。 具体取决于这些对象，可以将元素参数转换到相应的接口。 例如，如果表包含[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)对象，然后元素参数可强制转换为`IDiaSegment`接口。  
  
 它是更为常见的方法调用`QueryInterface`中的方法[IDiaTable](../../debugger/debug-interface-access/idiatable.md)相应枚举器接口的接口，并使用枚举器的特定方法表内容进行访问。 请参阅[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)有关示例的接口。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)