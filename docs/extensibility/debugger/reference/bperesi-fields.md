---
title: "BPERESI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPERESI_FIELDS"
helpviewer_keywords: 
  - "BPERESI_FIELDS 枚举"
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BPERESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定要检索的信息有关断点的一个失败的解决方法。  
  
## 语法  
  
```cpp#  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```c#  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## 成员  
 PERESI\_BPRESLOCATION  
 初始化\/使用 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 结构的 `bpResLocation` \(断点解析位置\) 字段。  
  
 BPERESI\_PROGRAM  
 初始化\/使用 `BP_ERROR_RESOLUTION_INFO` 结构的 `pProgram` 字段。  
  
 BPERESI\_THREAD  
 初始化\/使用 `BP_ERROR_RESOLUTION_INFO` 结构的 `pThread` 字段。  
  
 BPERESI\_MESSAGE  
 初始化\/使用 `BP_ERROR_RESOLUTION_INFO` 结构的 `bstrMessage` 字段。  
  
 BPERESI\_TYPE  
 初始化\/使用 `BP_ERROR_RESOLUTION_INFO` 结构的 `dwType` \(断点类型\) 字段。  
  
 BPERESI\_ALLFIELDS  
 初始化\/使用 `BP_ERROR_RESOLUTION_INFO` 结构的所有字段。  
  
## 备注  
 通过，参数传递给 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) 方法指示 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 结构的哪些字段进行初始化。  
  
 这些值也用于指示在 `BP_ERROR_RESOLUTION_INFO` 结构的哪些字段是使用和有效，当该结构返回时。  
  
 这些值可能按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)