---
title: "IDebugDocumentContext2::Compare |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentContext2::Compare
helpviewer_keywords: IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ed45c54b406d0e12a2909439755faf934f65941
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
比较到给定数组文档上下文中的此文档上下文。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>参数  
 `compare`  
 [in]取值范围为[DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)指定的比较类型的枚举。  
  
 `rgpDocContextSet`  
 [in]数组[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)表示正在相比文档上下文的对象。  
  
 `dwDocContextSetLen`  
 [in]文档上下文之间进行比较的数组的长度。  
  
 `pdwDocContext`  
 [out]返回到索引`rgpDocContextSet`满足的比较的第一个文档上下文的数组。  
  
## <a name="return-value"></a>返回值  
 返回`S_OK`如果找到匹配项。 返回`S_FALSE`如果没有找到匹配。 否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)数组中传递的对象必须实现相同的调试引擎实现`IDebugDocumentContext2`对象; 否则为调用比较不是有效。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)