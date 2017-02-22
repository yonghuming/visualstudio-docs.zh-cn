---
title: "IDebugDisassemblyStream2::Read | Microsoft Docs"
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
  - "IDebugDisassemblyStream2::Read"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Read"
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

从 " 反汇编流的当前位置开始阅读说明。  
  
## 语法  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```c#  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### 参数  
 `dwInstructions`  
 \[in\] 命令数拆分。  此值也是 `prgDisassembly` 数组的最大长度。  
  
 `dwFields`  
 \[in\] 指示标志的组合。 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) 枚举的 `prgDisassembly` 的哪些字段将完成。  
  
 `pdwInstructionsRead`  
 \[out\] 返回实际上是反汇编的命令数。  
  
 `prgDisassembly`  
 \[out\] 用反汇编的代码以填充的数组 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 结构，每个拆分的命令的结构。  此数组的长度由 `dwInstructions` 参数指定。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 可在当前范围命令的最大数量可通过调用 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) 方法获取。  
  
 下一条指令中的当前位置中调用 [查找](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) 方法更改读取。  
  
 `DSF_OPERANDS_SYMBOLS` 标志可以添加到 `dwFields` 参数的 `DSF_OPERANDS` 标志指示应使用符号名，在反汇编命令时。  
  
## 请参阅  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [查找](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)