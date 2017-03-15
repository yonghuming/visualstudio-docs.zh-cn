---
title: "Resources processor error/warning: &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.resx_generator_task"
ms.assetid: eb9a1bd0-7e63-4a2b-ad37-54f6e67d9b5a
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resources processor error/warning: &lt;reason&gt;
如果某个工具在处理 .resx 文件的过程中返回一个错误或警告，则会显示错误或警告的信息。  作为生成过程的一部分，项目系统会将每个 .resx 文件都转换为 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 资源管理器能理解的二进制文件。  该转换是使用进程内工具完成的。  
  
 此类错误或警告的最可能原因是 .resx 文件错误。  如果在 Visual Studio 外或者使用文本编辑器在 Visual Studio 内编辑了 .resx 文件，则该文件就可能被破坏。  
  
 这些文件通常是由 Windows 窗体和 Web 窗体设计器管理的。  
  
### 更正此错误  
  
1.  修复 .resx 文件的格式。  
  
     错误意味着未生成二进制文件，生成进程将失败。  警告只是为了提供一些信息。  
  
## 请参阅  
 [Resources in .Resx File Format](http://msdn.microsoft.com/zh-cn/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)