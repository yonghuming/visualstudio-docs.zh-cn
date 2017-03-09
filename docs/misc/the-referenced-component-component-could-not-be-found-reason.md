---
title: "The referenced component &#39;component&#39; could not be found. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.referencenotfound"
ms.assetid: 35491b4d-e3e4-4e7c-8ac1-3adb09c1ef58
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The referenced component &#39;component&#39; could not be found. &lt;reason&gt;
项目系统未能解析特定引用。  如果双击此任务列表项，会将焦点设置到解决方案资源管理器，并选择未能解析的引用。  
  
 编辑 [ReferencePaths](http://msdn.microsoft.com/zh-cn/8e549b39-7256-456a-8fd7-089b23facf9c) 属性以便在该路径中包含适当的目录。  
  
 如果将某项目移动到另外一台计算机上，可能发生此错误。  `ReferencePath` 属性以绝对路径的形式存储。  如果引用 R1 驻留在计算机 A 上的 c:\\R\\R1.dll 中，.vbproj.user 或 .csproj.user 文件就会将 c:\\R 作为 `ReferencePath` 属性的一部分存储。  但是，如果在计算机 B 上，R1 驻留在 d:\\R\\R1.dll 中，则因为 d:\\R 并不在引用路径上，因此项目系统将无法找到 R1。  
  
 一种类似的情况是源代码管理方案。  如果在项目中登记了 .vbproj.user（或 .csproj.user）文件，它并不会复制到您的计算机上，原因是该文件未存储在源代码管理中。  因此，`ReferencePath` 属性的初始值将为空白，并且依赖于 `ReferencePath` 获得解析的所有引用将无法解析。  有关更多信息，请参见*使用 Visual Studio .NET 和 Visual SourceSafe 进行组开发* 中的“管理依赖项”。  
  
 如果被引用项目不在当前解决方案中，也可能导致此错误。  
  
 当发生此错误时，项目就无法生成。  
  
 有关解析程序集引用的更多信息，请参见 [有关无效的引用的疑难解答](../ide/troubleshooting-broken-references.md)。  
  
## 请参阅  
 [管理项目中的引用](../ide/managing-references-in-a-project.md)