---
title: "PROCESS_INFO_FIELDS |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROCESS_INFO_FIELDS
helpviewer_keywords: PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5732b287512cb14ab885619799d0c885f69b791
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
指定要检索的进程的信息类型。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_PROCESS_INFO_FIELDS {   
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
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
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
  
## <a name="members"></a>成员  
 PIF_FILE_NAME  
 初始化/使用`bstrFileName`字段[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)结构。  
  
 PIF_BASE_NAME  
 初始化/使用`bstrBaseName`字段`PROCESS_INFO`结构。  
  
 PIF_TITLE  
 初始化/使用`bstrTitle`字段`PROCESS_INFO`结构。  
  
 PIF_PROCESS_ID  
 初始化/使用`ProcessId`字段`PROCESS_INFO`结构。  
  
 PIF_SESSION_ID  
 初始化/使用`dwSessionId`字段`PROCESS_INFO`结构。  
  
 PIF_ATTACHED_SESSION_NAME  
 初始化/使用`bstrAttachedSessionName`字段`PROCESS_INFO`结构。  
  
 PIF_CREATION_TIME  
 初始化/使用`CreationTime`字段`PROCESS_INFO`结构。  
  
 PIF_FLAGS  
 初始化/使用`Flags`字段`PROCESS_INFO`结构。  
  
 PIF_ALL  
 填写所有字段。  
  
## <a name="remarks"></a>备注  
 传递给[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)方法，以指示哪些字段[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)结构是否被初始化。  
  
 也用在`Fields`字段`PROCESS_INFO`结构以指示哪些字段是使用和有效。  
  
 这些标志可以与按位组合`OR`。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)