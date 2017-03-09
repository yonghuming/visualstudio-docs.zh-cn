---
title: "关于异常的疑难解答：System.Drawing.Printing.InvalidPrinterException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidPrinterException 类"
ms.assetid: e19b9b9c-2b0f-4839-85c0-ae75e1c356d2
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Drawing.Printing.InvalidPrinterException
当尝试使用无效的打印机设置访问打印机时，会引发 <xref:System.Drawing.Printing.InvalidPrinterException> 异常。  
  
## 相关提示  
 **确保打印机存在。**  
 无效打印机设置的最常见原因是引用不存在的打印机。 有关详细信息，请参阅<xref:System.Drawing.Printing>。  
  
 **确保已经安装默认打印机。**  
 如果未指定打印机，请确保安装了一个默认打印机。 有关详细信息，请参阅<xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>。  
  
## 请参阅  
 <xref:System.Drawing.Printing.InvalidPrinterException>   
 <xref:System.Drawing.Printing.PrinterSettings>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)