---
title: "DISASSEMBLY_STREAM_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_STREAM_FIELDS"
helpviewer_keywords: 
  - "DISASSEMBLY_STREAM_FIELDS 枚举"
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定检索的信息有关反汇编字段。  
  
## 语法  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## 成员  
 DSF\_ADDRESS  
 初始化\/使用 `bstrAddress` 字段。  
  
 DSF\_ADDRESSOFFSET  
 初始化\/使用 `bstrAddressOffset` 字段。  
  
 DSF\_CODEBYTES  
 初始化\/使用 `bstrCodeBytes` 字段。  
  
 DSF\_OPCODE  
 初始化\/使用 `bstrOpCode` 字段。  
  
 DSF\_OPERANDS  
 初始化\/使用 `bstrOperands` 字段。  
  
 DSF\_SYMBOL  
 初始化\/使用 `bstrSymbol` 字段。  
  
 DSF\_CODELOCATIONID  
 初始化\/使用 `uCodeLocationId` 字段。  
  
 DSF\_POSITION  
 初始化\/使用 `posBeg` 和 `posEnd` 字段。  
  
 DSF\_DOCUMENTURL  
 初始化\/使用 `bstrDocumentUrl` 字段。  
  
 DSF\_BYTEOFFSET  
 初始化\/使用 `dwByteOffset` 字段。  
  
 DSF\_FLAGS  
 初始化\/使用 `dwFlags` \([DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)\) 字段。  
  
 DSF\_OPERANDS\_SYMBOLS  
 包含符号名称。 `bstrOperands` 字段。  
  
 DSF\_ALL  
 用于反汇编流指定所有字段。  
  
## 备注  
 通过，参数传递给 [读取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 方法指示 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 结构的哪些字段进行初始化。  
  
 用于 `DisassemblyData` 结构的 `dwFields` 成员指示哪些字段是使用和有效，当结构返回。  
  
 这些值可能按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [读取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)