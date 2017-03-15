---
title: "注册 .NET Framework 的扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "“添加引用”对话框, 注册 .NET Framework 的扩展"
  - "MSBuild, 注册 .NET Framework 的扩展"
  - ".NET Framework 扩展, 注册"
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 注册 .NET Framework 的扩展
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以开发用于扩展 .NET Framework 的特定版本的程序集。  若要使程序集出现在 Visual Studio 的**“添加引用”**对话框中，您必须将包含该程序集的文件夹添加到系统注册表中。  
  
 例如，假定 Trey Research 公司开发了用于扩展 .NET Framework 4 的库，并且希望在项目以 .NET Framework 4 为目标时库程序集出现在**“添加引用”**对话框中。  还要假定程序集是在 32 位计算机上运行的 32 位程序集或在 64 位计算机上运行的 64 位程序集，并且这些程序集将安装在 C:\\TreyResearch\\Extensions4\\ 文件夹中。  
  
 使用此项注册此文件夹：HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\。  为该项提供默认值：C:\\TreyResearch\\Extensions4。  
  
> [!NOTE]
>  .NET Framework 版本的生成号可能不同。  
  
 若要在 64 位计算机上注册 32 位程序集，请使用 Wow6432 节点，例如：HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\。  
  
## 请参阅  
 [Visual Studio 集成](../msbuild/visual-studio-integration-msbuild.md)