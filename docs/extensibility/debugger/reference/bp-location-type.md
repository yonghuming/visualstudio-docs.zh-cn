---
title: "BP_LOCATION_TYPE | Microsoft Docs"
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
  - "BP_LOCATION_TYPE"
helpviewer_keywords: 
  - "BP_LOCATION_TYPE 结构"
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

为断点指定请求断点位置类型。  
  
## 语法  
  
```cpp#  
enum enum_BP_LOCATION_TYPE {   
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
  
```c#  
public enum enum_BP_LOCATION_TYPE {   
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
  
## 成员  
 BPLT\_NONE  
 未指定断点位置。  
  
 BPLT\_FILE\_LINE  
 指定断点位置类型作为文件行。  
  
 BPLT\_FUNC\_OFFSET  
 指定断点位置类型作为函数偏移量。  
  
 BPLT\_CONTEXT  
 指定断点位置类型作为上下文。  
  
 BPLT\_STRING  
 指定断点位置类型作为字符串。  
  
 BPLT\_ADDRESS  
 指定断点位置类型作为地址。  
  
 BPLT\_RESOLUTION  
 指定断点位置类型作为解析。  
  
 BPLT\_CODE\_FILE\_LINE  
 指定断点位置类型作为源代码行。  
  
 BPLT\_CODE\_FUNC\_OFFSET  
 指定断点位置类型，代码函数偏移量。  
  
 BPLT\_CODE\_CONTEXT  
 指定断点位置类型作为代码上下文。  
  
 BPLT\_CODE\_STRING  
 指定断点位置类型，编码字符串。  
  
 BPLT\_CODE\_ADDRESS  
 指定断点位置类型，代码地址。  
  
 BPLT\_DATA\_STRING  
 指定断点位置类型，数据字符串。  
  
 BPLT\_TYPE\_MASK  
 指定位掩码，因此，断点类型进行提取出该值。  
  
 BPLT\_LOCATION\_TYPE\_MASK  
 指定位掩码，因此，断点位置类型进行提取出该值。  
  
## 备注  
 参数形式传递给 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) 方法。  
  
 断点位置类型由断点类型和位置类型组成。  这意味着断点位置类型不是断点类型 \(例如，`BPT_CODE`\) 或位置类型 \(例如，`BPLT_FILE_LINE`\)。  当前支持的所有断点位置类型预定义的常量此枚举 \(`BPLT_CODE_FILE_LINE` 包括通过 `BPLT_DATA_STRING`\)。  
  
 `BPT_CODE` 和 `BPT_DATA` 是 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md) 枚举的成员。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)