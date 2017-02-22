---
title: "IDebugWindowsComputerPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugWindowsComputerPort2 接口"
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugWindowsComputerPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

查询有关目标计算机的信息允许。  
  
## 语法  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## 实现者说明  
 此接口由会议的端口对象实现调试管理器。  
  
## 方法  
 下表显示 `IDebugWindowsComputerPort2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|检索有关上运行调试器的计算机的信息。|  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll