---
title: "API 参考 （Visual Studio 调试） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ead1571856fa04e10103fbf2274dc0e22295154
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="api-reference-visual-studio-debugging"></a>API 参考 （Visual Studio 调试）
参考部分包括 API，显示的语法和用法的所有 API 元素的指南的概念性概述和多种类型的代码示例。 按类别按字母顺序列出的所有引用。  
  
 下表显示了常见`HRESULT`由方法返回的值。  
  
|名称|描述|值|  
|----------|-----------------|-----------|  
|S_OK|成功。|0x00000000|  
|E_UNEXPECTED|意外的失败。|: 0x8000FFFF|  
|E_NOTIMPL|未实现。|0x80004001|  
|E_OUTOFMEMORY|内存不足，无法完成操作。|已用完 0x8007000E|  
|E_INVALIDARG|一个或多个自变量均无效。|0x80070057|  
|E_NOINTERFACE|不支持此接口。|0x80004002|  
|E_POINTER|无效的指针。|0x80004003|  
|E_HANDLE|无效句柄。|0x80070006|  
|E_ABORT|操作中止。|0x80004004|  
|E_FAIL|意外的失败。|0x80004005|  
|E_ACCESSDENIED|常规拒绝访问错误。|0x80070005|  
  
> [!NOTE]
>  当[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]调试方法返回`S_OK`，假定所有缩小参数的指针是有效、 out 参数指针上执行任何验证，即当`S_OK`返回。  
  
> [!NOTE]
>  无效或`NULL`[out] 参数可能会导致崩溃 IDE。  
  
## <a name="see-also"></a>另请参阅  
 [接口](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SDK 适用于调试的帮助程序](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio 调试器可扩展性](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)