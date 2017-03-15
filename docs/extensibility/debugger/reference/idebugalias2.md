---
title: "IDebugAlias2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugAlias2 接口"
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugAlias2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 表示数字别名对于变量，并使 \(EE\) 来获取该别名的应用程序域的表达式计算器。  
  
## 语法  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## 实施者注意事项  
 通过托管的调试引擎 \(DE\) 实现此接口。  
  
## 方法  
 除了上方法 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 接口，此接口实现了以下方法︰  
  
|方法|描述|  
|--------|--------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|检索应用程序域的标识符。|  
  
## 备注  
 别名是以字符串形式的 \# 字符，例如，1001 \# 后跟十进制数。  
  
## 要求  
 标头︰ Ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll