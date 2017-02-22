---
title: "API 参考 (Visual Studio 调试) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]、 API 参考"
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# API 参考 (Visual Studio 调试)
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

引用部分包含演示语法和用法所有 API 元素的 API、教程和各种代码示例的概念性概述。  所有引用按类别按字母顺序列出。  
  
 下表显示方法返回的常见 `HRESULT` 值。  
  
|名称|说明|值|  
|--------|--------|-------|  
|S\_OK|成功。|0x00000000|  
|E\_UNEXPECTED|意外损坏。|0x8000FFFF|  
|E\_NOTIMPL|未实现。|0x80004001|  
|E\_OUTOFMEMORY|如果尚未完成操作足够的内存。|0x8007000E|  
|E\_INVALIDARG|一个或多个参数无效。|0x80070057|  
|E\_NOINTERFACE|不支持这样的接口。|0x80004002|  
|E\_POINTER|无效的指针。|0x80004003|  
|E\_HANDLE|无效处理。|0x80070006|  
|E\_ABORT|中止的操作。|0x80004004|  
|E\_FAIL|意外损坏。|0x80004005|  
|E\_ACCESSDENIED|泛型拒绝访问错误。|0x80070005|  
  
> [!NOTE]
>  在调试方法的 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 返回 `S_OK`，则，所有参数指针是有效的，也就是说，验证在参数指针未实现，当 `S_OK` 返回时。  
  
> [!NOTE]
>  无效或 `NULL` \[out\] 参数可能会导致 IDE 失败。  
  
## 请参阅  
 [接口](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SDK 帮助器调试](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio 调试器可扩展性](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)