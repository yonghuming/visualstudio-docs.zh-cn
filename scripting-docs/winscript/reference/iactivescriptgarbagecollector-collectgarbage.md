---
title: "IActiveScriptGarbageCollector::CollectGarbage |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07d5a00e04939331f85c4c74727aaf03b62814fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
活动脚本宿主调用此方法以开始垃圾回收。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>参数  
 `scriptgctype`  
 [in][SCRIPTGCTYPE 枚举](../../winscript/reference/scriptgctype-enumeration.md)，它指定是否执行全角或详尽垃圾回收。  
  
## <a name="return-value"></a>返回值  
 返回一个 HRESULT。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptGarbageCollector 接口](../../winscript/reference/iactivescriptgarbagecollector-interface.md)