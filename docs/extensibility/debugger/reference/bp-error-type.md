---
title: "BP_ERROR_TYPE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 10
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
ms.openlocfilehash: ab0dc686c4d002733bf8501be042e33c500fb8e3
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="bperrortype"></a>BP_ERROR_TYPE
指定断点的错误类型。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```csharp  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>成员  
 BPET_NONE  
 不指定任何断点错误。  
  
 BPET_TYPE_WARNING  
 指定警告样式断点错误。  
  
 BPET_TYPE_ERROR  
 指定了错误样式断点错误。  
  
 BPET_SEV_HIGH  
 指定高严重性断点错误。  
  
 BPET_SEV_GENERAL  
 指定的中等严重性断点错误。  
  
 BPET_SEV_LOW  
 指定的低严重性断点错误。  
  
 BPET_TYPE_MASK  
 指定掩码样式断点错误。  
  
 BPET_SEV_MASK  
 指定严重性掩码样式断点错误。  
  
 BPET_GENERAL_WARNING  
 指定常规警告样式断点错误。  
  
 BPET_GENERAL_ERROR  
 指定常规错误样式断点错误。  
  
 BPET_ALL  
 指定所有断点错误类型。  
  
## <a name="remarks"></a>备注  
 这些值可以与按位组合`OR`和用于`dwType`的成员[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)结构。 作为参数传递给传递[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)方法。  
  
 断点错误类型组成的类型和严重性。 这意味着该断点错误类型永远不会为刚类型 (例如， `BPET_TYPE_ERROR`，) 或严重级别 (例如， `BPET_SEV_GENERAL`) 本身。 `BPET_GENERAL_WARNING`和`BPET_GENERAL_ERROR`为常规的警告和错误断点提供预定义的值。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
