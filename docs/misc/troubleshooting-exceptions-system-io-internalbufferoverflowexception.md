---
title: "关于异常的疑难解答：System.IO.InternalBufferOverflowException | Microsoft Docs"
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
  - "InternalBufferOverflowException 类"
ms.assetid: 1f58ca15-c4e4-4af9-9a3d-42d2cf919cbe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.IO.InternalBufferOverflowException
内部缓冲区溢出时，将引发 <xref:System.IO.InternalBufferOverflowException> 异常。  
  
## 相关提示  
 **使用 FileSystemWatcher 时，筛选掉不需要的更改通知。**  
 在文件系统监视程序中，当被通知文件更改时，系统将那些更改存储到组件创建的缓冲区中，并将其传递给应用程序编程接口 \(API\)。 如果在短时间内有很多更改，则缓冲区可能溢出，导致 <xref:System.IO.InternalBufferOverflowException> 异常，从而丢失全部更改。 若要阻止缓冲区溢出，请使用 <xref:System.IO.FileSystemWatcher.NotifyFilter%2A> 和 <xref:System.IO.FileSystemWatcher.IncludeSubdirectories%2A> 属性筛选掉不需要的更改通知。 有关详细信息，请参阅<xref:System.IO.FileSystemWatcher>。  
  
## 备注  
 也可以通过 <xref:System.IO.FileSystemWatcher.InternalBufferSize%2A> 属性增加内部缓冲区的大小。 但是增加缓冲区的大小会影响性能，所以最好保持缓冲区尽可能小。  
  
## 请参阅  
 <xref:System.IO.InternalBufferOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)