---
title: "Could not bind to dependency &#39;assembly&#39; | Microsoft Docs"
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
  - "vs.tasklisterror.cantbinddependency"
ms.assetid: 0f76190d-d57e-4e0e-bec4-532aec978d08
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not bind to dependency &#39;assembly&#39;
项目的引用之一本身包含已找到的程序集引用（依赖项），但该程序集引用不是有效的程序集。  该错误将不会妨碍生成项目。  但是，可能会出现运行时错误。  
  
 这种情况意味着下列三种条件全部为真：  
  
-   磁盘上有多个文件具有相同的名称。  
  
-   其中有一个文件不是程序集，但是其他文件是程序集。  
  
-   引用路径首先搜索包含不是程序集的文件的目录。  
  
 **更正此错误**  
  
-   修改项目搜索目录和查找引用的顺序。  有关更多信息，请参见 [NIB: Reference Paths Dialog Box \(Visual Basic\)](http://msdn.microsoft.com/zh-cn/8e549b39-7256-456a-8fd7-089b23facf9c)。  
  
## 请参阅  
 [有关无效的引用的疑难解答](../ide/troubleshooting-broken-references.md)   
 [如何：使用“添加引用”对话框添加或移除引用](http://msdn.microsoft.com/zh-cn/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/zh-cn/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)