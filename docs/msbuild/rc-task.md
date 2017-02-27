---
title: "RC 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions"
  - "vc.task.rc"
  - "VC.Project.VCResourceCompilerTool.SuppressStartupBanner"
  - "VC.Project.VCResourceCompilerTool.NullTerminateStrings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), RC 任务"
  - "RC 任务 (MSBuild (Visual C++))"
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# RC 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包装 Microsoft Windows 资源编译器工具 rc.exe。  **RC** 任务将，例如游标、图标、位图、对话框和字体的资源编译为一个资源 \(.res\) 文件。  有关更多信息，请参见 [CodePlex](http://go.microsoft.com/fwlink/?LinkId=737) 网站上的“Resource Complier”（资源编译器）。  
  
## 参数  
 下表描述了  任务的参数。  大多数的任务参数和少数几个参数集对应于命令行选项。  
  
|Parameter|说明|  
|---------------|--------|  
|**AdditionalIncludeDirectories**|可选 **String\[\]** 参数。<br /><br /> 将目录添加到要在其中搜索包含文件的目录列表中。<br /><br /> 有关更多信息，请参见 MSDN 网站上 [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730)（使用 RC（RC 命令行））中的 **\/I** 选项。|  
|**AdditionalOptions**|可选 **String** 参数。<br /><br /> 命令行 optionsor 示例的列表，**"** *\/ option1 \/option2 \/option\#*"。  将此参数用于指定不用任何其他 **RC** 任务参数表示的命令行选项。<br /><br /> 有关更多信息，请参见 MSDN 网站上 [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730)（使用 RC（RC 命令行））中的选项.|  
|**Culture**|可选 **String** 参数。<br /><br /> 指定表示资源中使用的区域性的区域设置 ID。<br /><br /> 有关更多信息，请参见 MSDN 网站上 [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730)（使用 RC（RC 命令行））中的 **\/l** 选项。|  
|**IgnoreStandardIncludePath**|可选 **Boolean** 参数。<br /><br /> 如果为 `true`，则防止资源编译器搜索的头文件或资源文件时签 INCLUDE 环境变量。<br /><br /> 有关更多信息，请参见 MSDN 网站上 [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730)（使用 RC（RC 命令行））中的 **\/x** 选项。|  
|**NullTerminateStrings**|可选 **Boolean** 参数。<br /><br /> 如果为 `true`，则空终止字符串表中的所有字符串。<br /><br /> 有关更多信息，请参见 MSDN 网站上 [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730)（使用 RC（RC 命令行））中的 **\/n** 选项。|  
|**PreprocessorDefinitions**|可选 **String\[\]** 参数。<br /><br /> 定义一个或多个资源编译器预处理器符号。  指定宏符号的列表。<br /><br /> 有关更多信息，请参见 MSDN 网站上 [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730)（使用 RC（RC 命令行））中的 **\/d** 选项。  另请参见本表中的 **UndefinePreprocessorDefinitions**。|  
|**ResourceOutputFileName**|可选 **String** 参数。<br /><br /> 指定资源文件的名称。  指定源文件名。<br /><br /> 有关更多信息，请参见 MSDN 网站上 [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730)（使用 RC（RC 命令行））中的 **\/fo** 选项。|  
|**ShowProgress**|可选 **Boolean** 参数。<br /><br /> 如果为 `true`，则显示报告编译器进度的消息。<br /><br /> 有关更多信息，请参见 MSDN 网站上 [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730)（使用 RC（RC 命令行））中的 **\/v** 选项。|  
|**Source**|必选 `ITaskItem[]` 参数。<br /><br /> 定义可以由任务使用和发出的 MSBuild 源文件项数组。|  
|**SuppressStartupBanner**|可选 **Boolean** 参数。<br /><br /> 如果为 `true`，将在任务开始时防止显示版权和版本编号消息。<br /><br /> 有关更多信息，请键入 **\/?** 命令行选项，然后参见 **\/nologo** 选项。|  
|**TrackerLogDirectory**|可选 **String** 参数。<br /><br /> 指定跟踪日志的目录。|  
|**UndefinePreprocessorDefinitions**|要取消定义预处理器符号。<br /><br /> 有关更多信息，请参见 MSDN 网站上 [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730)（使用 RC（RC 命令行））中的 **\/u** 选项。  另请参见本表中的 **PreprocessorDefinitions**。|  
  
## 备注  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)