---
title: "PROCESS_INFO_FLAGS |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROCESS_INFO_FLAGS
helpviewer_keywords: PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 228b2d3286ad0b69a2eb813e18b8837ec038f28f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
本文介绍或指定的进程属性。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>成员  
 PIFLAG_SYSTEM_PROCESS  
 指示进程是一个系统进程。  
  
 PIFLAG_DEBUGGER_ATTACHED  
 指示由调试器调试该进程。 它可能是[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]可能某些其他调试器，例如，WinDbg 调试器，或它。  
  
 PIFLAG_PROCESS_STOPPED  
 指示该进程已停止。 有效才`PIFLAG_DEBUGGER_ATTACHED`还指定。 中提供[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]及更高版本。  
  
 PIFLAG_PROCESS_RUNNING  
 指示进程正在运行。 有效才`PIFLAG_DEBUGGER_ATTACHED`还指定。 中提供[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]及更高版本。  
  
## <a name="remarks"></a>备注  
 用于`Flags`的成员[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)结构。  
  
 这些标志可以与按位组合`OR`。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)