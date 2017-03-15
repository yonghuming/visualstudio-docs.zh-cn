---
title: "如何查明谁在传递错误的参数值？ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.parameters"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "调试 [C++], 参数"
  - "函数 [调试器], 检测错误参数值"
  - "参数值, 疑难解答"
  - "参数 [调试器]"
  - "传递参数, 值错误疑难解答"
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何查明谁在传递错误的参数值？
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 问题描述  
 给我的某个函数传递的是错误的参数值。  很多地方都在调用该函数。  如何查明是谁在传递错误值？  
  
## 解决方案  
  
#### 解决此问题  
  
1.  在函数的开始处设置一个位置断点。  
  
2.  右击该断点并选择**“条件”**。  
  
3.  在**“断点条件”**对话框中，单击**“条件”**复选框。  请参阅[高级断点](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)。  
  
4.  在文本框中输入一个表达式（例如 `Var==3`），此处 `Var` 是包含错误值的参数的名称，`3` 是传给此参数的错误值。  
  
5.  选择**“为真”**单选按钮，单击**“确定”**按钮。  
  
6.  现在再次运行程序。  当 `Var` 参数的值为 `3` 时，断点导致程序在函数开始处暂停。  
  
7.  然后可以使用“调用堆栈”窗口查找调用函数并定位到其源代码。  有关详细信息，请参阅[如何：使用“调用堆栈”窗口](../debugger/how-to-use-the-call-stack-window.md)。  
  
## 请参阅  
 [调试本机代码常见问题](../debugger/debugging-native-code-faqs.md)   
 [Breakpoints](http://msdn.microsoft.com/zh-cn/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [调试本机代码](../debugger/debugging-native-code.md)