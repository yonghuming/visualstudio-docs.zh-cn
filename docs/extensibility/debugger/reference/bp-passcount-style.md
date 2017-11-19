---
title: "BP_PASSCOUNT_STYLE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_PASSCOUNT_STYLE
helpviewer_keywords: BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58baa5aca9ef5bddf5d7060fdc88022952bc9ce3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
指定将导致激发该断点的断点传递计数与关联的条件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>成员  
 BP_PASSCOUNT_NONE  
 不指定任何断点传递计数样式。  
  
 BP_PASSCOUNT_EQUAL  
 设置断点传递计数样式为相等的。 当命中断点的次数等于传递计数，将引发断点。  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 将断点传递计数样式设置为大于或等于。 当命中断点的次数是等于或大于传递计数，将引发断点。  
  
 BP_PASSCOUNT_MOD  
 指定取模传递计数。 例如，如果传递计数是类型`BP_PASSCOUNT_MOD`和传递计数值为 4，断点激发每次命中的计数是 4 的倍数。  
  
## <a name="remarks"></a>备注  
 用于`stylePassCount`的成员[BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)反过来是的成员的结构[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)和[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)结构。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)