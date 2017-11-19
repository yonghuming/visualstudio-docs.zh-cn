---
title: "BP_RESOLUTION_LOCATION |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_RESOLUTION_LOCATION
helpviewer_keywords: BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8a7f722ea92e20bbceb7ed1bfe9eed31d23c32e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
指定断点解析位置的结构。  
  
## <a name="syntax"></a>语法  
  
```cpp  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```csharp  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## <a name="members"></a>成员  
 `bpType`  
 取值范围为[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)枚举，它指定如何解释`bpResLocation`联合或`unionmemberX`成员。  
  
 `bpResLocation.bpresCode`  
 [C + +]包含[BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)结构如果`bpType`  =  `BPT_CODE`。  
  
 `bpResLocation.bpresData`  
 [C + +]包含[BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)结构如果`bpType`  =  `BPT_DATA`。  
  
 `bpResLocation.unused`  
 [C + +]一个占位符。  
  
 `unionmember1`  
 [仅限 C#]请参阅关于如何解释的备注。  
  
 `unionmember2`  
 [仅限 C#]请参阅关于如何解释的备注。  
  
 `unionmember3`  
 [仅限 C#]请参阅关于如何解释的备注。  
  
 `unionmember4`  
 [仅限 C#]请参阅关于如何解释的备注。  
  
## <a name="remarks"></a>备注  
 此结构是的成员[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)和[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)结构。  
  
 [仅限 C#]`unionmemberX`成员会根据下表解释。 查看其左侧列`bpType`值然后跨以确定每个`unionmemberX`成员表示和封送`unionmemberX`相应地。 请参阅了如何解释此结构在 C# 中的示例。  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string`（数据表达式）|`string`（函数名称）|`string`（映像名称）|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>示例  
 此示例演示如何解释`BP_RESOLUTION_LOCATION`C# 中的结构。  
  
```csharp  
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
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)