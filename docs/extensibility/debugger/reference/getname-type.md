---
title: "GETNAME_TYPE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: GETNAME_TYPE
helpviewer_keywords: GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 06cb7cc6e882bbd1539b34035ca5a9be685512e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="getnametype"></a>GETNAME_TYPE
指定要从中检索文件的名称类型。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_GETNAME_TYPE {   
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
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>成员  
 GN_NAME  
 指定的友好名称的文档或上下文。  
  
 GN_FILENAME  
 指定的文档或上下文的完整路径。  
  
 GN_BASENAME  
 指定的基文件名称，而不是文档或上下文的完整路径。  
  
 GN_MONIKERNAME  
 在标记的窗体中指定的文档或上下文的唯一名称。  
  
 GN_URL  
 指定的文档或上下文的 URL 名称。  
  
 GN_TITLE  
 如果存在，请指定该文档的标题。  
  
 GN_STARTPAGEURL  
 获取进程起始页的 URL。  
  
## <a name="remarks"></a>备注  
 这些值作为参数传递[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)， [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)，和[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)方法以指定哪种类型的名称返回。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)