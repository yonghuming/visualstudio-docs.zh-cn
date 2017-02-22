---
title: "MODULE_INFO | Microsoft Docs"
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
  - "MODULE_INFO"
helpviewer_keywords: 
  - "MODULE_INFO 结构"
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述特定模块 \(DLL、 EXE 或程序集\)。  
  
## 语法  
  
```cpp#  
typedef struct tagMODULE_INFO {   
   MODULE_INFO_FIELDS dwValidFields;  
   BSTR               m_bstrName;  
   BSTR               m_bstrUrl;  
   BSTR               m_bstrVersion;  
   BSTR               m_bstrDebugMessage;  
   UINT64             m_addrLoadAddress;  
   UINT64             m_addrPreferredLoadAddress;  
   DWORD              m_dwSize;  
   DWORD              m_dwLoadOrder;  
   FILETIME           m_TimeStamp;  
   BSTR               m_bstrUrlSymbolLocation;  
   MODULE_FLAGS       m_dwModuleFlags;  
} MODULE_INFO;  
```  
  
```c#  
public struct MODULE_INFO {   
   public uint     dwValidFields;  
   public string   m_bstrName;  
   public string   m_bstrUrl;  
   public string   m_bstrVersion;  
   public string   m_bstrDebugMessage;  
   public ulong    m_addrLoadAddress;  
   public ulong    m_addrPreferredLoadAddress;  
   public uint     m_dwSize;  
   public uint     m_dwLoadOrder;  
   public FILETIME m_TimeStamp;  
   public string   m_bstrUrlSymbolLocation;  
   public uint     m_dwModuleFlags;  
};  
```  
  
## 成员  
 dwValidFields  
 标志的组合从指定的 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) 枚举的哪些字段。完成。  
  
 m\_bstrName  
 模块名。  
  
 m\_bstrUrl  
 模块 URL。  
  
 m\_bstrVersion  
 模块版本。  
  
 m\_bstrDebugMessage  
 有关模块的可选消息，例如， “符号无法加载”。  
  
 m\_addrLoadAddress  
 模块加载地址。  
  
 m\_addrPreferredLoadAddress  
 模块的首选加载地址。  
  
 m\_dwSize  
 模块范围。  
  
 m\_dwLoadOrder  
 模块加载顺序。  
  
 m\_TimeStamp  
 时间符号文件的上次更新。  
  
 m\_bstrUrlSymbolLocation  
 符号文件的位置 \(例如， “。  \\ "\) 指定在模块。  用于为一个起始位置查找模块的符号。  
  
 m\_dwModuleFlags  
 标志的组合。描述模块的 [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md) 枚举的。  
  
## 备注  
 此结构传递给该方法的 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) 方法。  
  
 此结构对应于 **模块** 窗口列出的每个模块。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)