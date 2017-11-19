---
title: "THREADPROPERTY_FIELDS |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: THREADPROPERTY_FIELDS
helpviewer_keywords: THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 626c4aa309c7ce68eaf5d97c734ec4fd731148c1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
指定要检索有关线程的哪些信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_THREADPROPERTY_FIELDS {   
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
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>成员  
 TPF_ID  
 初始化/使用`dwThreadId`字段[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)结构。  
  
 TPF_SUSPENDCOUNT  
 初始化/使用`dwSuspendCount`字段`THREADPROPERTIE`S 结构。  
  
 TPF_STATE  
 初始化/使用`dwThreadState`字段`THREADPROPERTIE`S 结构。  
  
 TPF_PRIORITY  
 初始化/使用`bstrPriority`字段`THREADPROPERTIE`S 结构。  
  
 TPF_NAME  
 初始化/使用`bstrName`字段`THREADPROPERTIE`S 结构。  
  
 TPF_LOCATION  
 初始化/使用`bstrLocation`字段`THREADPROPERTIE`S 结构。  
  
 TPF_ALLFIELDS  
 指定的所有字段。  
  
## <a name="remarks"></a>备注  
 这些值传递的自变量作为[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)方法，以指示哪些字段[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)结构是否被初始化。  
  
 这些值也用在`dwFields`的成员`THREADPROPERTIES`结构以指示哪些字段是使用和有效。  
  
 这些标志可以与按位组合`OR`。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)