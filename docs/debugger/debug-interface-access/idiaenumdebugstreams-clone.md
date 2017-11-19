---
title: "Idiaenumdebugstreams:: Clone |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumDebugStreams::Clone method
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c46f5a006cf5201e7a0cf46be6bd9beeeabe4264
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumdebugstreamsclone"></a>IDiaEnumDebugStreams::Clone
创建包含与当前的枚举器相同的枚举状态的枚举。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT Clone (   
   IDiaEnumDebugStreams** ppenum  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppenum`  
 [out]返回[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)对象，其中包含重复的枚举数。 流不会出现重复的仅枚举数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)