---
title: "IDebugDisassemblyStream2::Read |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::Read
helpviewer_keywords: IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0c75a832c2b9a59a681d6a80d087b69212a5361d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
读取 （从反汇编流中的当前位置开始） 的说明。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```csharp  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwInstructions`  
 [in]进行反汇编，对指令数。 该值也为的最大长度`prgDisassembly`数组。  
  
 `dwFields`  
 [in]中的标志的组合[DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)枚举，指示的哪些字段`prgDisassembly`要进行填写。  
  
 `pdwInstructionsRead`  
 [out]返回实际反汇编的指令的数。  
  
 `prgDisassembly`  
 [out]数组[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)填充的反汇编代码，每反汇编说明一个结构的结构。 根据来确定此数组的长度`dwInstructions`参数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 可以通过调用获取的最大的当前作用域中可用的指令数[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)方法。  
  
 从读取下一个指令的位置的当前位置可以更改通过调用[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)方法。  
  
 `DSF_OPERANDS_SYMBOLS`标志可以添加到`DSF_OPERANDS`中标记出来`dwFields`参数以指示反汇编说明时，应使用符号名。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [查找](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)