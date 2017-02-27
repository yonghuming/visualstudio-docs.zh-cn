---
title: "MODULE_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_FLAGS"
helpviewer_keywords: 
  - "MODULE_FLAGS 枚举"
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

用于描述模块。  
  
## 语法  
  
```cpp#  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```c#  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## 成员  
 MODULE\_FLAG\_NONE  
 不指定模块。  
  
 MODULE\_FLAG\_SYSTEM  
 指定系统模块。  
  
 MODULE\_FLAG\_SYMBOLS  
 指定符号模块。  
  
 MODULE\_FLAG\_64BIT  
 指定一个 64位模块。  
  
 MODULE\_FLAG\_OPTIMIZED  
 指定模块进行了优化。  此状态。 **模块** 窗口反映。  
  
 MODULE\_FLAG\_UNOPTIMIZED  
 指定模块未优化。  此状态。 **模块** 窗口反映。  这是默认状态。  
  
## 备注  
 用于 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) 结构的 `m_dwModuleFlags` 成员。  
  
 这些标志可以按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)