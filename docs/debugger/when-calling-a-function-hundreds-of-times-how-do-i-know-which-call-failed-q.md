---
title: "当一个函数被调用数百次时，如何确定哪次调用失败了？ | Microsoft Docs"
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
  - "vs.debug.functions"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "断点, 疑难解答"
  - "条件断点"
  - "错误 [调试器], 查找失败的函数调用"
  - "错误 [调试器], 函数调用"
  - "错误 [Visual Studio], 函数调用"
  - "失败"
  - "函数调用, 失败"
  - "函数 [调试器]"
  - "命中次数"
  - "位置断点调用失败"
  - "跳过计数"
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 当一个函数被调用数百次时，如何确定哪次调用失败了？
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 问题描述  
 程序在调用某函数（如 `CnvtV`）时失败。  失败以前该程序可能已调用了该函数数百次。  如果我在 `CnvtV` 上设置一个位置断点，程序在每次调用该函数时都停止，而我不希望这样。  我不知道什么条件导致调用失败，所以无法设置条件断点。  我该怎么办？  
  
## 解决方案  
 在函数上设置断点时可以将**“命中次数”**字段设置为一个大到永远无法达到的值。  在这种情况中，由于您确信函数 `CnvtV` 被调用了数百次，所以将**“命中次数”**设置为 1000 或更高。  然后运行程序，等待调用失败。  程序失败后，打开“断点”窗口并查看断点列表。  将显示您在 `CnvtV` 上设置的断点，其后跟着命中次数和剩余迭代次数：  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 现在您知道函数在第 101 次调用时失败。  如果重置断点，将命中次数设置为 101，然后再次运行程序，程序将在导致 `CnvtV` 调用失败的位置停止所有该调用。  
  
## 请参阅  
 [调试本机代码常见问题](../debugger/debugging-native-code-faqs.md)   
 [Setting Breakpoints](http://msdn.microsoft.com/zh-cn/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [调试本机代码](../debugger/debugging-native-code.md)