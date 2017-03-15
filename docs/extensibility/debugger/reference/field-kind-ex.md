---
title: "FIELD_KIND_EX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FIELD_KIND_EX 枚举"
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# FIELD_KIND_EX
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

枚举 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象可以包含的其他类型字段。  此枚举扩展 [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md) 枚举。  
  
## 语法  
  
```cpp#  
enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
} ;  
typedef DWORD FIELD_KIND_EX;  
```  
  
```c#  
public enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
};  
```  
  
## 成员  
 FIELD\_KIND\_EX\_NONE  
 字段不包含一个扩展类型。  
  
 FIELD\_TYPE\_EX\_METHODVAR  
 字段包含方法的变量。  
  
 FIELD\_TYPE\_EX\_CLASSVAR  
 字段包含类变量。  
  
## 要求  
 标题:Sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)