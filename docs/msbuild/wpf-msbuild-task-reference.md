---
title: "WPF MSBuild 任务引用 | Microsoft Docs"
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
  - "生成任务 [WPF MSBuild], Microsoft 生成引擎"
  - "使用 Microsoft 生成引擎来生成任务 [WPF MSBuild], 编译标记和进程资源"
  - "WPF MSBuild 任务参考 [WPF MSBuild]"
  - "WPF MSBuild 任务参考 [WPF MSBuild], 术语/定义表"
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# WPF MSBuild 任务引用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows Presentation Foundation \(WPF\) 生成过程用附加的一组生成任务（包括用于编译标记和处理资源的任务）扩展了 Microsoft Build Engine \(MSBuild\)。  
  
## 本节内容  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 将一组源资源分为将嵌入程序集中的资源。  如果资源不能本地化，则该资源将嵌入主应用程序集中，否则将嵌入附属程序集中。  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 如果项目中至少有一个[!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 页引用了在该项目中以本地方式声明的类型，则将生成一个程序集。  生成过程完成后或者如果生成过程失败，将会移除生成的程序集。  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 返回当前 [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)]运行时的目录。  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 将不可本地化的[!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 项目文件转换为编译的二进制格式。  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 对引用同一项目中的类型的[!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 文件执行第二次标记编译。  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 为整个程序集将本地化特性和一个或多个 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二进制格式文件的注释合并为一个文件。  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 将一个或多个资源（.jpg、.ico、.bmp、二进制格式的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]，以及其他扩展类型）嵌入一个 .resources 文件中。  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 检查、更新或移除唯一标识符 \(UID\)，以便本地化源 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 文件中包括的所有[!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 元素。  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 生成 [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] 项目时，将 **\<hostInBrowser \/\>** 元素添加到应用程序清单（*项目名*.exe.manifest）中。  
  
## 请参阅  
 [MSBuild](http://msdn.microsoft.com/zh-cn/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)