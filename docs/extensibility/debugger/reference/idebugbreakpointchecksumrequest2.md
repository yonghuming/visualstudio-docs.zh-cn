---
title: "IDebugBreakpointChecksumRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugBreakpointChecksumRequest2 接口"
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBreakpointChecksumRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示断点请求的文档校验和。  
  
## 语法  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## 实现者说明  
 实现由 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 调试包，并使用调试引擎。  
  
## 方法  
 下表显示 `IDebugBreakpointChecksumRequest2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|检索给定的断点请求的文档检查并检查和算法的唯一标识符使用。|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|确定检查和是否为此启用文档。|  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll