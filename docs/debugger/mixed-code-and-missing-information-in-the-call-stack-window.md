---
title: "“调用堆栈”窗口中的混合代码与丢失信息 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "托管代码，单步执行"
  - "“调用堆栈”窗口，混合模式调试"
  - "“调用堆栈”窗口，故障排除"
  - "本机框架"
  - "托管调用堆栈"
  - "混合模式调试，调用堆栈"
  - "单步执行，托管代码之外"
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# “调用堆栈”窗口中的混合代码与丢失信息
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

由于托管代码和本机代码的调用堆栈之间存在差异，因此对于混合的代码类型，调试器不能始终显示完整的调用堆栈。  本机代码调用托管代码时，您可能会注意到**“调用堆栈”**窗口中的内容与实际情况存在如下差异：  
  
-   紧邻托管代码之上的本机框架可能从**“调用堆栈”**窗口中消失。  有关详细信息，请参阅[如何：在“调用堆栈”窗口中缺少本机框架时跳出托管代码](../Topic/How%20to:%20Step%20out%20of%20Managed%20Code%20when%20Native%20Frames%20are%20Missing%20from%20the%20Call%20Stack%20Window.md)。  
  
-   对于在调试器以外启动的混合模式应用程序，**“调用堆栈”**窗口可能只显示托管代码，而不显示任何本机框架。  
  
 这两种情况都极为少见。  在多数对托管代码的本机调用中，都会正确显示调用堆栈。  
  
## 请参阅  
 [如何：使用“调用堆栈”窗口](../debugger/how-to-use-the-call-stack-window.md)