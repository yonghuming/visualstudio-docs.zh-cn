---
title: "Ijsdebugframe:: Getdocumentpositionwithname 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49afb5903e190280d226a24b22dc389041861c52
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName 方法
返回此堆栈帧用户级文档中的当前位置。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pDocumentName`  
 [out]对于静态脚本，指向文档的 URL。 对于动态脚本，将返回包含的类型的脚本 （例如，eval 代码，函数代码等） 的名称。  
  
 `pLine`  
 [out] 文档内的基于 1 的行位置。  
  
 `pColumn`  
 [out] 文档内的基于 1 的行位置。  
  
## <a name="return-value"></a>返回值  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>另请参阅  
 [IJsDebugFrame 接口](../../winscript/reference/ijsdebugframe-interface.md)