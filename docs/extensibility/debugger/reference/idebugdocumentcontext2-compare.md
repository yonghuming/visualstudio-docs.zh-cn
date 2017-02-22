---
title: "IDebugDocumentContext2::Compare | Microsoft Docs"
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
  - "IDebugDocumentContext2::Compare"
helpviewer_keywords: 
  - "IDebugDocumentContext2::Compare"
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

比较此文档上下文到特定数组文档上下文。  
  
## 语法  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```c#  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### 参数  
 `compare`  
 \[in\] 从指定比较的类型的 [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) 枚举的值。  
  
 `rgpDocContextSet`  
 \[in\] 数组中表示比较的文档上下文的 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 对象。  
  
 `dwDocContextSetLen`  
 \[in\] 数组的长度文档上下文比较。  
  
 `pdwDocContext`  
 \[out\] 返回索引。 `rgpDocContextSet` 数组第一个文档满足该比较的上下文。  
  
## 返回值  
 ，如果找到，则返回 `S_OK` 匹配。  ; 如果未找到，则返回 `S_FALSE` 匹配。  否则，返回错误代码。  
  
## 备注  
 该数组传递的 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 对象必须由同一实现调试实现对 `IDebugDocumentContext2` 对象的引擎;否则，此比较是无效的。  
  
## 请参阅  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)