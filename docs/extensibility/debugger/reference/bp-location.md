---
title: "BP_LOCATION | Microsoft Docs"
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
  - "BP_LOCATION"
helpviewer_keywords: 
  - "BP_LOCATION 联合"
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定用于结构的类型描述断点的位置。  
  
## 语法  
  
```cpp#  
typedef struct _BP_LOCATION {  
   BP_LOCATION_TYPE bpLocationType;  
   union {  
      BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;  
      BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;  
      BP_LOCATION_CODE_CONTEXT     bplocCodeContext;  
      BP_LOCATION_CODE_STRING      bplocCodeString;  
      BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;  
      BP_LOCATION_DATA_STRING      bplocDataString;  
      BP_LOCATION_RESOLUTION       bplocResolution;  
      DWORD                        unused;  
   } bpLocation;  
} BP_LOCATION;  
```  
  
```c#  
public struct BP_LOCATION {  
   public uint   bpLocationType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public IntPtr unionmember4;  
};  
```  
  
## 成员  
 `bpLocationType`  
 从使用的 [BP\_LOCATION\_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) 枚举的值解释 `bpLocation` 联合或 `unionmemberX` 成员。  
  
 `bpLocation`.`bplocCodeFileLine`  
 只有 C\+\+ \[\] 包含 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) 结构，如果 `bpLocationType` \= `BPLT_CODE_FILE_LINE`。  
  
 `bpLocation.bplocCodeFuncOffset`  
 只有 C\+\+ \[\] 包含 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) 结构，如果 `bpLocationType` \= `BPLT_CODE_FUNC_OFFSET`。  
  
 `bpLocation.bplocCodeContext`  
 只有 C\+\+ \[\] 包含 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) 结构，如果 `bpLocationType` \= `BPLT_CODE_CONTEXT`。  
  
 `bpLocation.bplocCodeString`  
 只有 C\+\+ \[\] 包含 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) 结构，如果 `bpLocationType` \= `BPLT_CODE_STRING`。  
  
 `bpLocation.bplocCodeAddress`  
 只有 C\+\+ \[\] 包含 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) 结构，如果 `bpLocationType` \= `BPLT_CODE_ADDRESS`。  
  
 `bpLocation.bplocDataString`  
 只有 C\+\+ \[\] 包含 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) 结构，如果 `bpLocationType` \= `BPLT_DATA_STRING`。  
  
 `bpLocation.bplocResolution`  
 只有 C\+\+ \[\] 包含 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) 结构，如果 `bpLocationType` \= `BPLT_RESOLUTION`。  
  
 `unionmember1`  
 \[仅限于 c\#\] 请参见有关如何的备注解释。  
  
 `unionmember2`  
 \[仅限于 c\#\] 请参见有关如何的备注解释。  
  
 `unionmember3`  
 \[仅限于 c\#\] 请参见有关如何的备注解释。  
  
 `unionmember4`  
 \[仅限于 c\#\] 请参见有关如何的备注解释。  
  
## 备注  
 此结构是 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 和 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 结构的成员。  
  
 \[仅限于 c\#\] `unionmemberX` 成员根据下表解释。  查找在左列下为 `bpLocationType` 值和其他列之间找到确定每个 `unionmemberX` 成员表示并相应地排列 `unionmemberX` 。  请参见下面的示例中的方式解释此结构的一部分 \(在 c\# 中\)  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string` \(上下文\)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|\-|\-|  
|`BPLT_CODE_FUNC_OFFSET`|`string` \(上下文\)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|\-|\-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPLT_CODE_STRING`|`string` \(上下文\)|`string` \(条件表达式\)|\-|\-|  
|`BPLT_CODE_ADDRESS`|`string` \(上下文\)|`string` \(模块的 URL\)|`string` \(函数名\)|`string` \(地址\)|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` \(上下文\)|`string` \(数据表达式\)|`uint` \(元素的数字\)|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|\-|\-|\-|  
  
## 示例  
 此示例演示如何解释 c\# 中 `BP_LOCATION` framework `BPLT_DATA_STRING` 类型的。  此特定类型演示如何解释所有四个 `unionmemberX` 成员的所有可能的格式 \(对象、字符串和数字\)。  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_LOCATION bp)  
        {  
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)  
            {  
                 IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
                 string context = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);  
            }  
        }  
    }  
}  
```  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)   
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)   
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)   
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)   
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)