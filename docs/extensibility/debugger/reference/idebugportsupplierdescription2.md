---
title: "IDebugPortSupplierDescription2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierDescription2 接口"
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

使 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI 显示在 **附加的进程** 对话框的 **将信息传输** 部分的内部文本。  
  
## 语法  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## 实现者说明  
 此接口由端口提供程序实现。  
  
## 方法  
 下表显示 `IDebugPortSupplierDescription2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|检索说明和说明元数据端口提供程序的。|  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll