---
title: "BP_RESOLUTION_LOCATION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_RESOLUTION_LOCATION"
helpviewer_keywords: 
  - "BP_RESOLUTION_LOCATION 结构"
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定断点解析位置的结构。  
  
## 语法  
  
```cpp#  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```c#  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## 成员  
 `bpType`  
 从指定如何解释 `bpResLocation` 联合或 `unionmemberX` 成员的 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md) 枚举的值。  
  
 `bpResLocation.bpresCode`  
 只有 C\+\+ \[\] 包含 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) 结构，如果 `bpType` \= `BPT_CODE`。  
  
 `bpResLocation.bpresData`  
 只有 C\+\+ \[\] 包含 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) 结构，如果 `bpType` \= `BPT_DATA`。  
  
 `bpResLocation.unused`  
 只有 C\+\+ \[\] 的占位符。  
  
 `unionmember1`  
 \[仅限于 c\#\] 请参见有关如何的备注解释。  
  
 `unionmember2`  
 \[仅限于 c\#\] 请参见有关如何的备注解释。  
  
 `unionmember3`  
 \[仅限于 c\#\] 请参见有关如何的备注解释。  
  
 `unionmember4`  
 \[仅限于 c\#\] 请参见有关如何的备注解释。  
  
## 备注  
 此结构是 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 和 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 结构的成员。  
  
 \[仅限于 c\#\] `unionmemberX` 成员根据下表解释。  查找在左列下为 `bpType` 值然后确定每个 `unionmemberX` 成员表示并相应地排列 `unionmemberX` 。  请参见示例以方式解释 c\# 的此结构。  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPT_DATA`|`string` \(数据表达式\)|`string` \(函数名\)|`string` 图像 \(名称\)|`enum_BP_RES_DATA_FLAGS`|  
  
## 示例  
 此示例演示如何解释 c\# 中 `BP_RESOLUTION_LOCATION` 结构。  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_RESOLUTION_LOCATION bprl)  
        {  
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)  
            {  
                 IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
            }  
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)  
            {  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;  
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
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP\_RES\_DATA\_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)