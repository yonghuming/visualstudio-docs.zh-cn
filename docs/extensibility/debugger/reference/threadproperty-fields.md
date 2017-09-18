---
title: "THREADPROPERTY_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADPROPERTY_FIELDS"
helpviewer_keywords: 
  - "THREADPROPERTY_FIELDS 枚举"
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定有关线程的信息进行检索。  
  
## 语法  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```c#  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## 成员  
 TPF\_ID  
 初始化\/使用 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) 结构的 `dwThreadId` 字段。  
  
 TPF\_SUSPENDCOUNT  
 初始化\/使用 `THREADPROPERTIE`的结构的 `dwSuspendCount` 字段。  
  
 TPF\_STATE  
 初始化\/使用 `THREADPROPERTIE`的结构的 `dwThreadState` 字段。  
  
 TPF\_PRIORITY  
 初始化\/使用 `THREADPROPERTIE`的结构的 `bstrPriority` 字段。  
  
 TPF\_NAME  
 初始化\/使用 `THREADPROPERTIE`的结构的 `bstrName` 字段。  
  
 TPF\_LOCATION  
 初始化\/使用 `THREADPROPERTIE`的结构的 `bstrLocation` 字段。  
  
 TPF\_ALLFIELDS  
 指定所有字段。  
  
## 备注  
 这些值传递，因为参数。 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) 方法指示 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) 结构的哪些字段进行初始化。  
  
 这些值也用于 `THREADPROPERTIES` 结构的 `dwFields` 成员指示哪些字段是使用和有效。  
  
 这些标志可以按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)