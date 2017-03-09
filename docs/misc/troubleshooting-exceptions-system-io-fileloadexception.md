---
title: "关于异常的疑难解答：System.IO.FileLoadException | Microsoft Docs"
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
  - "FileLoadException 类"
ms.assetid: 6b4519e3-4d29-4031-8aec-c2735b4ee16d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.IO.FileLoadException
如果找到托管程序集但不能加载，则会引发 <xref:System.IO.FileLoadException> 异常。  
  
## 相关提示  
 **确保文件是有效的 .NET Framework 程序集。**  
 如果文件不是有效的 .NET Framework 程序集，则会引发此异常。 有关详细信息，请参阅<xref:System.Reflection.Assembly>。  
  
 **确保一个程序集或模块不会用两个不同的证据加载两次。**  
 证据是输入安全策略决策的一组信息（如代码可授予哪些权限）。 有关详细信息，请参见<xref:System.EnterpriseServices.Internal.Publish.GacRemove%2A>和<xref:System.Reflection.Assembly.Evidence%2A>  
  
 **如果使用 RegisterAssembly 或 UnregisterAssembly 方法，请确保程序集名称的长度不超过 MAX\_PATH 个字符。**  
 程序集名称的长度不能超过 MAX\_PATH。 有关详细信息，请参阅<xref:System.EnterpriseServices.Internal.IComSoapPublisher.RegisterAssembly%2A>和<xref:System.EnterpriseServices.Internal.IComSoapPublisher.UnRegisterAssembly%2A>。  
  
 **如果加载附属程序集，请确保指定的 CultureInfo 与文件的 CultureInfo 匹配。**  
 附属程序集包含本地化资源，这些资源包含单个区域性（用作默认或非特定区域性）的非本地化可执行代码和资源。 有关详细信息，请参阅<xref:System.Reflection.Assembly.GetSatelliteAssembly%2A>。  
  
## 请参阅  
 <xref:System.IO.FileLoadException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)