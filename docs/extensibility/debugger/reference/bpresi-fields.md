---
title: "BPRESI_FIELDS |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BPRESI_FIELDS
helpviewer_keywords: BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90bd76940ea2b442d0f2aecdf28ebceb6e995ca1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="bpresifields"></a>BPRESI_FIELDS
指定要检索有关断点的成功的解决方法的信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## <a name="members"></a>成员  
 BPRESI_BPRESLOCATION  
 初始化/使用`bpResLocation`（断点解析位置） 字段[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)结构。  
  
 BPRESI_PROGRAM  
 初始化/使用`pProgram`字段`BP_RESOLUTION_INFO`结构。  
  
 BPRESI_THREAD  
 初始化/使用`pThread`字段`BP_RESOLUTION_INFO`结构。  
  
 BPRESI_ALLFIELDS  
 指定的所有字段。  
  
## <a name="remarks"></a>备注  
 传递给[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)方法，以指示哪些字段[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)结构是否被初始化。  
  
 这些标志也用于指示哪些字段`BP_RESOLUTION_INFO`结构均使用和有效时返回该结构。  
  
 这些值可以与按位组合`OR`。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)