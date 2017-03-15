---
title: "关于异常的疑难解答：System.ObjectDisposedException | Microsoft Docs"
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
  - "ObjectDisposedException 类, 故障排除"
ms.assetid: 702912b6-e927-4f8e-8b7c-2e1880312b0e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.ObjectDisposedException
如果尝试操作已释放的对象（如已关闭的流或注册表项），则会引发 <xref:System.ObjectDisposedException> 异常。  
  
## 相关提示  
 **在尝试使用资源前，请确保该资源还未释放。**  
 例如，如果尝试操作流，请确保它在此之前未被关闭。  
  
## 请参阅  
 <xref:System.ObjectDisposedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)