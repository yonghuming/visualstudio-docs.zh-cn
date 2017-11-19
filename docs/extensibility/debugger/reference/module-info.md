---
title: "MODULE_INFO |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MODULE_INFO
helpviewer_keywords: MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5d86bf829c904acd56ca9ab37aa94a0f4038214
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="moduleinfo"></a>MODULE_INFO
描述特定模块 （DLL、 EXE 或程序集）。  
  
## <a name="syntax"></a>语法  
  
```cpp  
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
  
```csharp  
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
  
## <a name="members"></a>成员  
 dwValidFields  
 中的标志的组合[MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)指定哪些字段填出的枚举。  
  
 m_bstrName  
 模块名。  
  
 m_bstrUrl  
 模块 URL 中。  
  
 m_bstrVersion  
 该模块版本。  
  
 m_bstrDebugMessage  
 可选的消息，有关该模块，例如，"无法加载符号。"  
  
 m_addrLoadAddress  
 模块加载地址。  
  
 m_addrPreferredLoadAddress  
 模块的首选的负载地址。  
  
 m_dwSize  
 模块的大小。  
  
 m_dwLoadOrder  
 模块加载顺序。  
  
 m_TimeStamp  
 符号文件上次修改时间。  
  
 m_bstrUrlSymbolLocation  
 符号文件的位置 (例如，"。\\") 指定模块中。 用作查找模块的符号的起始位置。  
  
 m_dwModuleFlags  
 中的标志的组合[MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)描述该模块的枚举。  
  
## <a name="remarks"></a>备注  
 此结构传递给[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)方法中填充位置。  
  
 此结构对应于中列出每个模块**模块**窗口。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)