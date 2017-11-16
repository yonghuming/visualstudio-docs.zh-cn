---
title: "marker_importance 枚举 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords: Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d09138f90b94d3b37c4a20fbe53f311fa29a36e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="markerimportance-enumeration"></a>marker_importance 枚举
表示并发可视化工具标记的重要性级别。  
  
## <a name="syntax"></a>语法  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>成员  
  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`critical_importance`|指定该标记具有关键重要性。|  
|`high_importance`|指定该标记具有高重要性。|  
|`low_importance`|指定该标记具有低重要性。|  
|`normal_importance`|指定该标记具有普通重要性。|  
  
## <a name="requirements"></a>要求  
 **标头：**cvmarkersobj.h  
  
 **命名空间：**Concurrency::diagnostic  
  
## <a name="see-also"></a>另请参阅  
 [diagnostic 命名空间](../profiling/diagnostic-namespace.md)