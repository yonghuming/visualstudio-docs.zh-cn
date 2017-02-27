---
title: "EncUnavailableReason | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EncUnavailableReason"
helpviewer_keywords: 
  - "EncUnavailableReason 枚举"
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# EncUnavailableReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`This is for internal use only!` 表示原因 **" 编辑并继续 "** 不可用。  
  
## 语法  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```c#  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### 参数  
 ENCUN\_NONE  
 特定原因 " 编辑并继续 " 不可用。  
  
 ENCUN\_INTEROP  
 编辑并继续 "，在互操作期间不可用的调用。  
  
 ENCUN\_SQLCLR  
 编辑并继续 "，在使用公共语言运行时的 SQL 期间不可用的过程调用 \(CLR\)。  
  
 ENCUN\_MINIDUMP  
 ， " 编辑并继续 " 不可用，在处理和转储时。  
  
 ENCUN\_EMBEDDED  
 ， " 编辑并继续 " 不可用，在处理嵌入式代码时。  
  
 ENCUN\_ATTACH  
 ， " 编辑并继续 " 不可用，因为该会话附加到，不生成，调试器。  
  
 ENCUN\_WIN64  
 ， " 编辑并继续 " 不可用，在处理 64 位 windows 代码时。  
  
## 备注  
 此枚举仅供内部使用由 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]。  [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) 和 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) 方法实现的由自定义端口提供程序应始终返回 `E_NOTIMPL`。  
  
## 要求  
 标题:msdbg.idl  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)