---
title: "关于异常的疑难解答：System.Windows.Xps.XpsWriterException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHWXXpsWriter"
helpviewer_keywords: 
  - "System.Windows.Xps.XpsWriterException 异常"
  - "XpsWriterException 异常"
ms.assetid: 3b9fbb94-ed67-44f2-82bb-af5cb5ada1ef
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Windows.Xps.XpsWriterException
当调用的 <xref:System.Windows.Xps.XpsWriterException> 或 <xref:System.Windows.Xps.XpsDocumentWriter> 对象的方法与对象的当前状态不兼容时，将引发 <xref:System.Windows.Xps.VisualsToXpsDocument> 异常。  
  
## 备注  
 例如，如果在对象未执行异步写操作时调用任一对象类型的 `CancelAsync` 方法，则会引发此异常。  
  
## 请参阅  
 <xref:System.Windows.Xps.XpsWriterException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)