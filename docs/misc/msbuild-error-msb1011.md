---
title: "MSBuild 错误 MSB1011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.AmbiguousProjectError"
helpviewer_keywords: 
  - "MSB1011"
ms.assetid: f3cb16e5-288c-4dba-941f-a0ed3bf92db7
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB1011
**此文件夹中包含多个项目或解决方案文件，请指定要使用的项目或解决方案文件。**  
  
 如果命令行上未指定项目文件，则 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 将在当前工作目录中搜索一个具有以“proj”或“sln”结尾的文件扩展名的文件，并使用该文件。  当前工作目录中包含多个文件扩展名以“proj”或“sln”结尾的文件。  
  
### 更正此错误  
  
1.  在命令行上包括项目文件名。  例如，不是键入 `msbuild`，而是键入 `msbuild myapp.proj`。  
  
## 请参阅  
 [命令行参考](../msbuild/msbuild-command-line-reference.md)