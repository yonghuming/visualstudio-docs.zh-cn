---
title: "关于异常的疑难解答：System.DeploymentFramework.DeploymentDownloadException | Microsoft Docs"
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
  - "DeploymentDownloadException 类"
  - "应用程序部署 [C#]，DeploymentDownloadException 类"
  - "部署应用程序 [C#]，DeploymentDownloadException 类"
ms.assetid: 55ec7af5-b1d1-4db2-8af8-3c708f521cc7
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.DeploymentFramework.DeploymentDownloadException
在下载应用程序更新时发生任何类型的网络异常，都会引发 `T:System.DeploymentFramework.DeploymentDownloadException`。  
  
## 相关提示  
 **检查 InnerException 以确定基础 System.Net 或基础 System.IO 异常。**  
 在下载应用程序更新时，只要出现网络异常，都会引发此异常。 检查异常的 <xref:System.Exception.InnerException%2A> 属性以确定基础异常。  
  
## 请参阅  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Try...Catch...Finally 语句](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)