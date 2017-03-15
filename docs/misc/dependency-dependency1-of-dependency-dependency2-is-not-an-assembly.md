---
title: "依赖项“dependency2”的依赖项“dependency1”不是程序集 | Microsoft Docs"
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
  - "vs.tasklisterror.notcomplusassembly2"
ms.assetid: e3b96601-458e-40de-81ea-ddcae9b42996
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 依赖项“dependency2”的依赖项“dependency1”不是程序集
项目系统已经确定程序集 \(dependency2\) 的特定依赖项 \(dependency1\) 不是 .NET 程序集。  
  
 **更正此错误**  
  
-   重新安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]（如果该程序集附带 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或 .NET Framework）。  
  
     \- 或 \-  
  
-   重新安装相应的第三方控件。  
  
     此错误将不会妨碍生成项目。 但是，可能会出现运行时错误。  
  
## 请参阅  
 [有关无效的引用的疑难解答](../ide/troubleshooting-broken-references.md)   
 [NIB 如何：使用“添加引用”对话框添加或删除引用](http://msdn.microsoft.com/zh-cn/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/zh-cn/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)