---
title: "Ijsdebugprocess:: Createstackwalker 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugProcess.CreateStackWalker
apilocation: jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66ca7594f4e3c6ef44aa8cde1d92f17d46a9aa30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>IJsDebugProcess::CreateStackWalker 方法
堆栈查看器的工厂方法。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>参数  
 `threadId`  
 [in]线程 id。  
  
 `ppStackWalker`  
 [out]新堆栈查看器对象。  
  
## <a name="return-value"></a>返回值  
  
## <a name="remarks"></a>备注  
 如果线程不具有在其上的 JavaScript，则返回 E_JsDEBUG_UNKNOWN_THREAD。 目标进程停止时，可能仅调用此方法。  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>另请参阅  
 [IJsDebugProcess 接口](../../winscript/reference/ijsdebugprocess-interface.md)