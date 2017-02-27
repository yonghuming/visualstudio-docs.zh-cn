---
title: "PROCESS_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FLAGS"
helpviewer_keywords: 
  - "PROCESS_INFO_FLAGS 枚举"
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述或指定进程的属性。  
  
## 语法  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```c#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## 成员  
 PIFLAG\_SYSTEM\_PROCESS  
 指示进程是系统进程。  
  
 PIFLAG\_DEBUGGER\_ATTACHED  
 指示进程由调试器调试。  它可以是 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 调试器，也可能是其他一些调试器，例如， WinDbg。  
  
 PIFLAG\_PROCESS\_STOPPED  
 指示进程将停止。  有效，仅当 `PIFLAG_DEBUGGER_ATTACHED` 还指定。  在 [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] 及更高版本中提供。  
  
 PIFLAG\_PROCESS\_RUNNING  
 指示运行的进程。  有效，仅当 `PIFLAG_DEBUGGER_ATTACHED` 还指定。  在 [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] 及更高版本中提供。  
  
## 备注  
 用于 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) 结构的 `Flags` 成员。  
  
 这些标志可以按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)