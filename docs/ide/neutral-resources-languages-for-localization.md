---
title: "用于本地化的非特定资源语言 | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "区域性, 查找资源"
  - "全球化 [Visual Studio], 资源"
  - "本地化 [Visual Studio], 资源"
  - "非特定语言资源"
  - "NeutralResourcesLanguageAttribute 类"
  - "资源 [Visual Studio], 回调系统"
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 用于本地化的非特定资源语言
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:System.Resources.NeutralResourcesLanguageAttribute> 类指定主程序集中包含的资源的区域性。  此特性用于性能增强，因此 <xref:System.Resources.ResourceManager> 对象不搜索包括主程序集中包含的资源。  
  
 下面的代码说明如何设置非特定资源语言。  该代码可以放置在生成脚本中，或者 AssemblyInfo.vb 或 AssemblyInfo.cs 文件中。  
  
```vb#  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```c#  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## 请参阅  
 <xref:System.Resources.ResourceManager>   
 [介绍基于 .NET Framework 的国际应用程序](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [用于本地化的资源的分层组织](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [本地化应用程序](../ide/localizing-applications.md)   
 [对应用程序进行全球化和本地化](../ide/globalizing-and-localizing-applications.md)