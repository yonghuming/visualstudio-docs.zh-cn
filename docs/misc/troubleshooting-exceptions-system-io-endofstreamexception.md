---
title: "关于异常的疑难解答：System.IO.EndOfStreamException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "EndOfStreamException 类"
ms.assetid: 1271e6f6-3a0d-49f0-9ff4-178d480687be
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.IO.EndOfStreamException
当尝试读取超出流末尾的内容时，将引发 <xref:System.IO.EndOfStreamException> 异常。  
  
## 相关提示  
 **在读取操作之前检查是否到达了文件的结尾。**  
 使用 <xref:System.IO.StreamReader.Peek%2A> 方法在读取流之前检查文件的结尾。  
  
## 请参阅  
 <xref:System.IO.EndOfStreamException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [如何：对新建的数据文件进行读取和写入](../Topic/How%20to:%20Read%20and%20Write%20to%20a%20Newly%20Created%20Data%20File.md)   
 [如何：打开并追加到日志文件](../Topic/How%20to:%20Open%20and%20Append%20to%20a%20Log%20File.md)