---
title: "关于异常的疑难解答：System.Printing.PrintingCanceledException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PrintingCanceledException 异常"
  - "System.Printing.PrintingCanceledException 异常"
ms.assetid: bec418d6-f168-4a73-962f-5ee0427600b6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Printing.PrintingCanceledException
当代码尝试访问已取消的打印作业时，将出现 <xref:System.Printing.PrintingCanceledException> 异常。  
  
## 备注  
 如果正在创建的 Windows Presentation Foundation \(WPF\) 应用程序包含打印功能且允许取消打印作业，请务必正确处理此异常。 此类型的未经处理的异常会导致 Windows Presentation Foundation 应用程序停止响应。  
  
## 请参阅  
 <xref:System.Printing.PrintingCanceledException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)