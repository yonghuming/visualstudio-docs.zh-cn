---
title: "未能将文件“file”添加到项目。 &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_no_add_file"
ms.assetid: 8bd70556-596a-4e24-a71c-a340604ee93d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 未能将文件“file”添加到项目。 &lt;reason&gt;
无法将已从 .vbproj 或 .csproj 文件中读取的文件添加到项目中。 原因包括：  
  
-   文件名无效。  
  
-   文件在路径内。 例如，如果你有项目相对路径 File1\\File2.txt，但还存在一个具有相对路径 File1\\File2.txt 的文件夹。  
  
-   项已存在。 当某个文件在项目文件中列出两次时将发生这种情况。  
  
-   链接已存在。[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 和 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项目系统有一个限制，即每个项目中只能有一个具有相同名称的链接。 意思是，例如，项目的文件夹 A 和文件夹 B 中不能同时具有指向 file.vb 的链接。  
  
 手动编辑项目文件很可能导致此错误。  
  
 为其显示此诊断的任何文件将不会添加到项目中。  
  
## 请参阅  
 [项目文件](/visual-cpp/ide/project-files)   
 [NIB：项目中的项管理](http://msdn.microsoft.com/zh-cn/762e606b-7f44-4b66-97a1-e30a703654a0)