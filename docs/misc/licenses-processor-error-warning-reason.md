---
title: "Licenses processor error/warning: &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.licx_generator_task"
ms.assetid: 85750198-7bd3-4936-b1eb-954dcc3ff573
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Licenses processor error/warning: &lt;reason&gt;
如果某个工具在处理 .licx 文件的过程中返回一个错误或警告，则会显示错误或警告的信息。  作为生成过程的一部分，项目系统会将 Licenses.licx 文件（如果有的话）转换为 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 许可证管理器可理解的二进制文件。  该转换是使用进程内工具完成的。  
  
 此类错误或警告的最可能原因是 .licx 文件错误。  如果使用文本编辑器在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 外或 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内编辑了 .licx 文件，则该文件就可能被破坏。  
  
 这些文件通常是由 Windows 窗体和 Web 窗体设计器管理的。  
  
### 更正此错误  
  
1.  修复 .licx 文件的格式。  
  
     错误意味着未生成二进制文件，生成进程将失败。  警告只是为了提供一些信息。  
  
## 请参阅  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/zh-cn/f793852c-da06-4d52-a826-65f635844772)