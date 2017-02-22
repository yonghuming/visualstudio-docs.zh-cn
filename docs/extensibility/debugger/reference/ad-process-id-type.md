---
title: "AD_PROCESS_ID_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AD_PROCESS_ID_TYPE"
helpviewer_keywords: 
  - "AD_PROCESS_ID_TYPE 枚举"
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定如何解释在 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) 结构的进程 ID。  
  
## 语法  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```c#  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## 成员  
 AD\_PROCESS\_ID\_SYSTEM  
 进程 ID 是系统标识符。  使用 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) 结构的 `ProcessId.dwProcessId` 字段。  
  
 AD\_PROCESS\_ID\_GUID  
 进程 ID 是 GUID。  使用 `AD_PROCESS_ID` 结构的 `ProcessId.guidProcessId` 字段。  
  
## 备注  
 用于 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) 结构的 `ProcessIdType` 成员识别类型进程在结构包含的 ID。  确定如何解释结构中的 `ProcessId` 联合。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)