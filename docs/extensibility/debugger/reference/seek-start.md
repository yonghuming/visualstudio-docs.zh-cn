---
title: "SEEK_START | Microsoft Docs"
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
  - "SEEK_START"
helpviewer_keywords: 
  - "SEEK_START 枚举"
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# SEEK_START
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定开始查找 " 反汇编流中的位置。  
  
## 语法  
  
```cpp#  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```c#  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## 成员  
 SEEK\_START\_BEGIN  
 寻求在本的开头当前文件。  
  
 SEEK\_START\_END  
 寻求到的末尾的开头当前文件。  
  
 SEEK\_START\_CURRENT  
 寻求在当前位置开始当前文件。  
  
 SEEK\_START\_CODECONTEXT  
 查找特定代码上下文的开头当前文件。  
  
 SEEK\_START\_CODELOCID  
 查找特定代码位置标识符的开头。  代码位置标识符通过调用 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)获取。  
  
## 备注  
 将作为参数传递 [查找](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) 方法。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [查找](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)