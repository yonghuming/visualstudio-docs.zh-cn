---
title: "Ijsdebugframe:: Evaluate 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.Evaluate
apilocation: jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38e826048e85456ca63e069de67701b1fc3e9f04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate 方法
计算表达式的上下文中的此堆栈帧。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pExpressionText`  
 [in]要计算的表达式。  
  
 `ppDebugProperty`  
 [out]表示属性浏览器对象。  
  
 `pError`  
 [out]错误消息中，如果发生错误。  
  
## <a name="return-value"></a>返回值  
  
## <a name="remarks"></a>备注  
 将返回以下:，则为 S_OK： 评估成功，* ppDebugProperty 包含计算结果。 S_FALSE： 评估引发错误 （或不支持的求值运算）， \*pError 包含错误消息。  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>另请参阅  
 [IJsDebugFrame 接口](../../winscript/reference/ijsdebugframe-interface.md)