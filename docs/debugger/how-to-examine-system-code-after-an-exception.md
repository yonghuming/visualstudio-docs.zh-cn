---
title: "如何：在发生异常后检查系统代码 | Microsoft Docs"
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
helpviewer_keywords: 
  - "调试, 异常"
  - "异常, 调试"
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何：在发生异常后检查系统代码
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

发生异常时，您可能需要检查系统调用内部的代码，以确定该异常的起因。  如果您没有为系统代码加载符号，或者启用了“仅我的代码”，则下面的步骤说明了如何执行此操作。  
  
### 在发生异常后检查系统代码  
  
1.  在**“调用堆栈”**窗口中右击，然后单击**“显示外部代码”**。  
  
     如果未启用“仅我的代码”，则快捷菜单中不提供此选项，默认情况下显示系统代码。  
  
2.  右击此时显示在**“调用堆栈”**窗口中的外部代码帧。  
  
3.  指向**“加载符号”**，然后单击**“Microsoft 符号服务器”**。  
  
    1.  如果启用了“仅我的代码”，则将显示一个对话框。  它指出“仅我的代码”现在已禁用。  要单步执行系统调用，必须这样做。  
  
    2.  将出现**“正在下载公共符号”**对话框。  下载完毕后会自动关闭该对话框。  
  
4.  现在即可在**“调用堆栈”**窗口和其他窗口中检查系统代码。  例如，您可以双击调用堆栈帧在源窗口或**“反汇编”**窗口中查看代码。  
  
## 请参阅  
 [管理调试器的异常](../debugger/managing-exceptions-with-the-debugger.md)