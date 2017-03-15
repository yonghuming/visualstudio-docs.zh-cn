---
title: "MSBuild 响应文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - ".rsp 文件"
  - "MSBuild, .rsp 文件"
  - "MSBuild, 响应文件"
  - "响应文件, MSBuild"
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# MSBuild 响应文件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

响应 \(.rsp\) 文件是包含 MSBuild.exe 命令行开关的文本文件。  可以每个开关位于单独的一行中，也可以所有开关都位于一行中。  注释行以 **\#** 符号开头。  **@** 开关用于将另一个响应文件传递给 MSBuild.exe。  
  
 自动响应文件是一个特殊的 .rsp 文件，生成项目时 MSBuild.exe 会自动使用该文件。  文件 MSBuild.rsp 必须与 MSBuild.exe 位于同一目录中，否则会找不到它。  您可以编辑此文件来指定 MSBuild.exe 的默认命令行开关。  例如，如果您每次生成项目时都使用相同的记录器，则可以将 **\/logger** 开关添加到 MSBuild.rsp，MSBuild.exe 就会在每次生成项目时使用该记录器。  
  
## 请参阅  
 [MSBuild 参考](../msbuild/msbuild-reference.md)   
 [命令行参考](../msbuild/msbuild-command-line-reference.md)