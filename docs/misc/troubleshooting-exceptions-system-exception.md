---
title: "关于异常的疑难解答：System.Exception | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Exception 异常"
  - "基类, 异常"
  - "异常, 基类"
ms.assetid: fc15931a-9323-47c6-a42f-55d0534b939a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Exception
表示在应用程序执行过程中发生的错误。 它是所有异常的基类。  
  
## 相关提示  
 **有关更多信息，请参见 InnerException 属性。**  
 若要修复该错误，可能需要导致当前异常的内部（或先前）异常的信息。 当前异常的 <xref:System.Exception.InnerException%2A> 属性中含有内部异常。 可以使用**“异常助手”**对话框中的**“查看详细信息”**链接来访问 <xref:System.Exception.InnerException%2A> 属性。  
  
 **暂时关闭“仅我的代码”调试。**  
 异常也有可能发生在不是您编写的代码中。 若要调试这些代码，必须关闭“仅我的代码”调试。 有关更多信息，请参见[“选项”对话框 \-\>“调试”\-\>“常规”](../debugger/general-debugging-options-dialog-box.md)。  
  
## 请参阅  
 <xref:System.Exception>   
 <xref:System.Exception.InnerException%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [如何：在引发异常时中断](../misc/how-to-break-when-an-exception-is-thrown.md)   
 [“选项”对话框 \-\>“调试”\-\>“常规”](../debugger/general-debugging-options-dialog-box.md)