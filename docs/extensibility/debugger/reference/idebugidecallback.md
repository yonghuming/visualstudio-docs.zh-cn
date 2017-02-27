---
title: "IDebugIDECallback | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugIDECallback 接口"
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugIDECallback
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 启用要在调试器的输出窗口中显示一条消息的表达式计算器 \(EE\)。  
  
## 语法  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## 实施者注意事项  
 通过托管的调试引擎实现该回调。  
  
## 调用方的说明  
 由表达式计算器将输出发送到调试器的输出窗口，可以使用它。  
  
## 方法  
 此接口实现以下方法︰  
  
|方法|描述|  
|--------|--------|  
|[DisplayMessage](../Topic/IDebugIDECallback::DisplayMessage.md)|将指定的消息字符串发送到调试器的输出窗口。|  
  
## 要求  
 标头︰ Ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll