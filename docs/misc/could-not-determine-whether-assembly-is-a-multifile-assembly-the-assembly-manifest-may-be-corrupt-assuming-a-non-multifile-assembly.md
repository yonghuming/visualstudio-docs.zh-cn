---
title: "无法确定“assembly”是否为多文件程序集。 程序集清单可能已损坏。 假定一个非多文件程序集。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.unknownscatterstatusforcopy"
ms.assetid: be49d3f2-b091-488c-8579-e27ef09d9c80
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 无法确定“assembly”是否为多文件程序集。 程序集清单可能已损坏。 假定一个非多文件程序集。
由于项目系统无法读取你项目所引用的程序集，从而导致其无法确定你是否正在引用一个多文件程序集。 因此，该程序集可能不会正确复制到输出目录。  
  
 **更正此错误**  
  
-   重新安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]（如果该程序集附带 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或 .NET Framework）。  
  
     \- 或 \-  
  
-   重新安装相应的第三方控件。  
  
     此错误将不会妨碍生成项目。 但是，可能会出现运行时错误。  
  
## 请参阅  
 [有关无效的引用的疑难解答](../ide/troubleshooting-broken-references.md)   
 [NIB 如何：使用“添加引用”对话框添加或删除引用](http://msdn.microsoft.com/zh-cn/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/zh-cn/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)