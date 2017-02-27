---
title: "DISASSEMBLY_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_FLAGS"
helpviewer_keywords: 
  - "DISASSEMBLY_FLAGS 枚举"
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

用于反汇编指定标志。  
  
## 语法  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## 成员  
 DF\_DOCUMENTCHANGE  
 指示此命令比前一个在其他文档。  
  
 DF\_DISABLED  
 指示此命令不会执行。  
  
 DF\_INSTRUCTION\_ACTIVE  
 指示此命令是其中一命令执行 \(可以有多个\)。  
  
 DF\_DATA  
 指示此命令实际上是数据 \(不是代码\)。  
  
 DF\_HASSOURCE  
 指示此命令具有源。  这些命令，例如分析或垃圾回收代码，没有相应的源。  
  
 DF\_DOCUMENT\_CHECKSUM  
 指示 `bstrDocumentUrl` 字段在以后包含检查和数据文档 URL。  说明如何的 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 结构请参见 " 备注 " 部分中检查和数据。  
  
## 备注  
 用作 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 结构的 `dwFlags` 成员。  
  
 这些标志可以按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)