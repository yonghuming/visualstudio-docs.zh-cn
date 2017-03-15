---
title: "PROCESS_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FIELDS"
helpviewer_keywords: 
  - "PROCESS_INFO_FIELDS 枚举"
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定了检索哪种信息进程。  
  
## 语法  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```c#  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## 成员  
 PIF\_FILE\_NAME  
 初始化\/使用 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) 结构的 `bstrFileName` 字段。  
  
 PIF\_BASE\_NAME  
 初始化\/使用 `PROCESS_INFO` 结构的 `bstrBaseName` 字段。  
  
 PIF\_TITLE  
 初始化\/使用 `PROCESS_INFO` 结构的 `bstrTitle` 字段。  
  
 PIF\_PROCESS\_ID  
 初始化\/使用 `PROCESS_INFO` 结构的 `ProcessId` 字段。  
  
 PIF\_SESSION\_ID  
 初始化\/使用 `PROCESS_INFO` 结构的 `dwSessionId` 字段。  
  
 PIF\_ATTACHED\_SESSION\_NAME  
 初始化\/使用 `PROCESS_INFO` 结构的 `bstrAttachedSessionName` 字段。  
  
 PIF\_CREATION\_TIME  
 初始化\/使用 `PROCESS_INFO` 结构的 `CreationTime` 字段。  
  
 PIF\_FLAGS  
 初始化\/使用 `PROCESS_INFO` 结构的 `Flags` 字段。  
  
 PIF\_ALL  
 填写所有字段。  
  
## 备注  
 传递给 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) 方法指示 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) 结构的哪些字段进行初始化。  
  
 还用于在 `Fields``PROCESS_INFO` 结构字段指示哪些字段是使用和有效。  
  
 这些标志可以按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)