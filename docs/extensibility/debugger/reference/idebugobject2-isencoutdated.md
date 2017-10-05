---
title: "IDebugObject2::IsEncOutdated |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 8
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 7161f3e608390e5a513faf86b2e0b7ed2459deed
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
此方法确定此对象或父容器的编辑并继续状态是否已过期。 自定义表达式计算器不实现此方法，始终返回`E_NOTIMPL`。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pfEncOutdated`  
 [out]非零 (`TRUE`) 的编辑并继续状态为已过期，如果零 (`FALSE`) 如果不是。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
> [!NOTE]
>  应始终返回自定义表达式计算器`E_NOTIMPL`。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
