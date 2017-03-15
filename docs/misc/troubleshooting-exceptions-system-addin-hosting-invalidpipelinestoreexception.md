---
title: "关于异常的疑难解答：System.AddIn.Hosting.InvalidPipelineStoreException | Microsoft Docs"
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
  - "InvalidPipelineStoreException 异常"
  - "System.AddIn.Hosting.InvalidPipelineStoreException 异常"
ms.assetid: d12556bc-5cfd-481c-a27b-46ee2571e646
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.AddIn.Hosting.InvalidPipelineStoreException
当未找到目录以及用户无权访问管线根路径或外接程序路径时，将引发 <xref:System.AddIn.Hosting.InvalidPipelineStoreException> 异常。  
  
## 备注  
 与 <xref:System.IO.DirectoryNotFoundException> 不同的是，此异常未提供任何路径信息。 这样可以阻止恶意用户故意指定错误路径并使用异常返回的信息来确定实际路径。  
  
 该异常由以下将生成和更新外接程序和管线信息的存储区的发现方法引发：<xref:System.AddIn.Hosting.AddInStore.FindAddIns%2A>、<xref:System.AddIn.Hosting.AddInStore.Rebuild%2A>、<xref:System.AddIn.Hosting.AddInStore.RebuildAddIns%2A>、<xref:System.AddIn.Hosting.AddInStore.Update%2A> 和 <xref:System.AddIn.Hosting.AddInStore.UpdateAddIns%2A>。  
  
## 请参阅  
 <xref:System.AddIn.Hosting.InvalidPipelineStoreException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)