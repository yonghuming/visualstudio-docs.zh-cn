---
title: "MODULE_INFO_FIELDS | Microsoft Docs"
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
  - "MODULE_INFO_FIELDS"
helpviewer_keywords: 
  - "MODULE_INFO_FIELDS 枚举"
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定标志对于调试模块信息。  
  
## 语法  
  
```cpp#  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## 成员  
 MIF\_NONE  
 初始化\/使用未在结构中的字段。  
  
 MIF\_NAME  
 初始化\/使用在 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) 结构的 `m_bstrName` 字段。  
  
 MIF\_URL  
 初始化\/使用在 `MODULE_INFO` 结构的 `m_bstrUrl` 字段。  
  
 MIF\_VERSION  
 初始化\/使用在 `MODULE_INFO` 结构的 `m_bstrVersion` 字段。  
  
 MIF\_DEBUGMESSAGE  
 初始化\/使用在 `MODULE_INFO` 结构的 `m_bstrDebugMessage` 字段。  
  
 MIF\_LOADADDRESS  
 初始化\/使用在 `MODULE_INFO` 结构的 `m_addrLoadAddress` 字段。  
  
 MIF\_PREFFEREDADDRESS  
 初始化\/使用在 `MODULE_INFO` 结构的 `m_addrPreferredLoadAddress` 字段。  
  
 MIF\_SIZE  
 初始化\/使用在 `MODULE_INFO` 结构的 `m_dwSize` 字段。  
  
 MIF\_LOADORDER  
 初始化\/使用在 `MODULE_INFO` 结构的 `m_dwLoadOrder` 字段。  
  
 MIF\_TIMESTAMP  
 初始化\/使用在 `MODULE_INFO` 结构的 `m_TimeStamp` 字段。  
  
 MIF\_URLSYMBOLLOCATION  
 初始化\/使用在 `MODULE_INFO` 结构的 `m_bstrUrlSymbolLocation` 字段。  
  
 MIF\_FLAGS  
 初始化\/使用在 `MODULE_INFO` 结构的 `m_dwModuleFlags` 字段。  
  
 MIF\_ALLFIELDS  
 对 `MODULE_INFO` 结构的字段的初始化\/使用所有。  
  
## 备注  
 这些值传递，因为参数。 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) 方法指示 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) 结构的哪些字段进行初始化。  
  
 这些值也用于 `MODULE_INFO` 结构指示哪些字段是使用和有效。  
  
 这些标志可以按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)