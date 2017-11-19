---
title: "AD_PROCESS_ID_TYPE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AD_PROCESS_ID_TYPE
helpviewer_keywords: AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 75904ef6e06ef7ccd6d126091f8ec0fbe523ac9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
指定如何解释的进程 ID [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)结构。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>成员  
 AD_PROCESS_ID_SYSTEM  
 进程 ID 是一个系统标识符。 使用`ProcessId.dwProcessId`字段[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)结构。  
  
 AD_PROCESS_ID_GUID  
 进程 ID 是一个 GUID。 使用`ProcessId.guidProcessId`字段`AD_PROCESS_ID`结构。  
  
## <a name="remarks"></a>备注  
 用于`ProcessIdType`的成员[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)结构来标识类型包含在结构中的进程 ID。 确定如何解释`ProcessId`联合结构中。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)