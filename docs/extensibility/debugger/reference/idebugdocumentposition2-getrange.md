---
title: "IDebugDocumentPosition2::GetRange |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentPosition2::GetRange
helpviewer_keywords: IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c1ea17c8125aea6c962c0562095ea8fba680f8b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
获取此文档位置的范围。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pBegPosition`  
 [在中，out]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)使用的起始位置填充的结构。 如果不需要此信息，请将此参数设置为 null 值。  
  
 `pEndPosition`  
 [在中，out]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)使用结束位置填充的结构。 如果不需要此信息，请将此参数设置为 null 值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 在一个位置断点的文档位置中指定的范围是调试引擎 (DE) 用于搜索提前实际影响代码的语句。 例如，考虑以下代码：  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 第 5 行分配给正在调试的程序的任何代码。 如果第 5 行设置断点调试器想 DE 向前搜索一定影响代码的第一行，调试器会指定一系列，包括的其他候选行断点可能正确放置。 DE 将然后向前搜索这些行直到它找到可以接受断点的行。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)