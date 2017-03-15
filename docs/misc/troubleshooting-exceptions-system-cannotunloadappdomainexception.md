---
title: "关于异常的疑难解答：System.CannotUnloadAppDomainException | Microsoft Docs"
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
  - "CannotUnloadAppDomainException 类"
ms.assetid: eeee07c3-fdbc-4c91-859b-a419d23be9ba
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.CannotUnloadAppDomainException
当尝试卸载下面的某一项时会引发 <xref:System.CannotUnloadAppDomainException> 异常：  
  
-   默认的应用程序域，该域在应用程序的整个生命周期内必须保持加载状态  
  
-   带有的正在运行的线程且该线程无法立即停止执行的应用程序域  
  
-   已经卸载的应用程序域  
  
## 相关提示  
 **确保您尝试卸载的应用程序域不是默认域、没有正在运行的线程并且尚未卸载。**  
 这些条件中的任何一个都将引发此异常。 有关更多信息，请参见<xref:System.AppDomain.Unload%2A>。  
  
## 请参阅  
 <xref:System.CannotUnloadAppDomainException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)