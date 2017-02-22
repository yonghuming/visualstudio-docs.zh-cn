---
title: "GETNAME_TYPE | Microsoft Docs"
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
  - "GETNAME_TYPE"
helpviewer_keywords: 
  - "GETNAME_TYPE 枚举"
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定文件的名称类型检索。  
  
## 语法  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```c#  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## 成员  
 GN\_NAME  
 指定文档或上下文的友好名称。  
  
 GN\_FILENAME  
 指定文档或上下文的完整路径。  
  
 GN\_BASENAME  
 指定一个基文件名而不是文档或上下文的完整路径。  
  
 GN\_MONIKERNAME  
 以标记形式，指定文档或上下文的唯一名称。  
  
 GN\_URL  
 指定文档或上下文的 URL 名称。  
  
 GN\_TITLE  
 ，如果存在，指定文档的标题。  
  
 GN\_STARTPAGEURL  
 获取开始的页 URL 进程。  
  
## 备注  
 这些值作为参数传递给 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)、 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)和 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) 方法返回指定哪一类型的名称。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)