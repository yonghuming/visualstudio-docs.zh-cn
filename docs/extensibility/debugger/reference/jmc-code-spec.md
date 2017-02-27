---
title: "JMC_CODE_SPEC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "JMC_CODE_SPEC"
helpviewer_keywords: 
  - "JMC_CODE_SPEC 结构"
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# JMC_CODE_SPEC
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此机制用于设置模块的 JustMyCode 信息。  
  
## 语法  
  
```cpp#  
typedef struct _JMC_CODE_SPEC {  
   BOOL fIsUserCode;  
   BSTR bstrModuleName;  
} JMC_CODE_SPEC;  
```  
  
```c#  
public struct JMC_CODE_SPEC {  
   public int    fIsUserCode;  
   public string bstrModuleName;  
};  
```  
  
## 成员  
 fIsUserCode  
 非零 \(`TRUE`\)，如果模块将被视为用户代码;否则，零 \(0\)`FALSE`\)，如果模块会将外部代码和不进行调试。  
  
 bstrModuleName  
 相关的模块的名称。  
  
## 备注  
 此结构将作为列表这样的结构。 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) 方法。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)