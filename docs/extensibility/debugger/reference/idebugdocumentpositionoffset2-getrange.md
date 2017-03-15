---
title: "IDebugDocumentPositionOffset2::GetRange |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d14c212a3cb4499996ba6cf4d73d0b2fca73f7bc
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
检索当前的文档位置的范围。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```c#  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdwBegOffset`  
 [in、 out]为范围的起始位置的偏移量。 如果不需要此信息，请将此参数设置为 null 值。  
  
 `pdwEndOffset`  
 [in、 out]为范围的结束位置的偏移量。 如果不需要此信息，请将此参数设置为 null 值。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 在一个位置断点的文档位置中指定的范围内通过调试引擎 (DE) 用于继续搜索实际贡献代码的语句。 例如，考虑以下代码：  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 第 5 行分配给正在调试的程序的任何代码。 如果将在第 5 行设置断点调试器想 DE 向前搜索一定量的贡献代码的第一行，调试器将指定包含其他候选行断点可能会正确放一个范围。 DE 将然后向前搜索这些行直到找到可以接受断点的行。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
