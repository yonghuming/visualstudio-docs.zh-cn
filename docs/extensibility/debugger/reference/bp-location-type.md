---
title: "BP_LOCATION_TYPE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_TYPE
helpviewer_keywords: BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7db6cbd73ba45d05b878648101a7643f21879076
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
指定断点请求断点的位置类型。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```csharp  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## <a name="members"></a>成员  
 BPLT_NONE  
 指定没有断点位置。  
  
 BPLT_FILE_LINE  
 指定为文件行的断点的位置类型。  
  
 BPLT_FUNC_OFFSET  
 指定断点的位置类型作为函数偏移量。  
  
 BPLT_CONTEXT  
 上下文指定断点的位置类型。  
  
 BPLT_STRING  
 指定断点的位置类型为字符串。  
  
 BPLT_ADDRESS  
 为地址中指定的断点的位置类型。  
  
 BPLT_RESOLUTION  
 指定断点的位置类型来解决此问题。  
  
 BPLT_CODE_FILE_LINE  
 作为源代码的行中指定的断点的位置类型。  
  
 BPLT_CODE_FUNC_OFFSET  
 为代码函数偏移量为指定的断点的位置类型。  
  
 BPLT_CODE_CONTEXT  
 作为代码上下文中指定的断点的位置类型。  
  
 BPLT_CODE_STRING  
 代码字符串形式指定的断点的位置类型。  
  
 BPLT_CODE_ADDRESS  
 为代码地址指定的断点的位置类型。  
  
 BPLT_DATA_STRING  
 指定为数据字符串的断点的位置类型。  
  
 BPLT_TYPE_MASK  
 指定一个位掩码，以便可以利用值中提取的断点类型。  
  
 BPLT_LOCATION_TYPE_MASK  
 指定一个位掩码，以便可以利用值提取断点位置类型。  
  
## <a name="remarks"></a>备注  
 作为参数传递给传递[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)方法。  
  
 断点位置类型组成断点类型和位置类型。 这意味着该断点位置类型永远不会为刚断点类型 (例如， `BPT_CODE`) 或位置类型 (例如， `BPLT_FILE_LINE`)。 此枚举中包含当前支持的所有断点位置类型的预定义的常量 (`BPLT_CODE_FILE_LINE`通过`BPLT_DATA_STRING`)。  
  
 `BPT_CODE`和`BPT_DATA`成员的[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)枚举。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)