---
title: "BscMake 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.bscmake"
  - "VC.Project.VCBscMakeTool.PreserveSBR"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "BscMake 任务 (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), 任务"
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# BscMake 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio IDE 不再使用 bscmake。  自 Visual Studio 2008 起，浏览信息自动存储在解决方案文件夹的 .sdf 文件中。  
  
 包装 Microsoft 浏览信息维护实用工具 \(bscmake.exe\)。  Bscmake.exe 工具从在编译期间创建的源浏览器文件 \(.sbr\) 生成浏览信息文件 \(.bsc\)。  可使用**对象浏览器**查看 .bsc 文件。  有关详细信息，请参阅 [BSCMAKE 参考](/visual-cpp/build/reference/bscmake-reference)。  
  
## 参数  
 下表描述了 **BscMake**  任务的参数。  大多数任务参数都对应于命令行选项。  
  
|参数|描述|  
|--------|--------|  
|**AdditionalOptions**|可选 **String** 参数。<br /><br /> 在命令行上指定的选项列表。  例如，“\/*option1* \/*option2* \/*option\#*”。  使用此参数可指定未由任何其他 **BscMake** 任务参数表示的选项。<br /><br /> 有关详细信息，请参阅 [BSCMAKE 选项](/visual-cpp/build/reference/bscmake-options)中的选项。|  
|**OutputFile**|可选 **String** 参数。<br /><br /> 指定重写默认输出文件名的文件名。<br /><br /> 有关详细信息，请参阅 [BSCMAKE 选项](/visual-cpp/build/reference/bscmake-options)中的 **\/o** 选项。|  
|**PreserveSBR**|可选 **Boolean** 参数。<br /><br /> 如果为 `true`，则会强制非增量生成。  无论 .bsc 文件是否存在，都会发生完整的非增量生成，并防止 .sbr 文件被截断。<br /><br /> 有关详细信息，请参阅 [BSCMAKE 选项](/visual-cpp/build/reference/bscmake-options)中的 **\/n** 选项。|  
|**Sources**|可选 **ITaskItem\[\]** 参数。<br /><br /> 定义可以被任务使用和发出的 MSBuild 源文件项的数组。|  
|**SuppressStartupBanner**|可选 **Boolean** 参数。<br /><br /> 如果为 `true`，则任务开始时会阻止版权和版本号消息显示。<br /><br /> 有关详细信息，请参阅 [BSCMAKE 选项](/visual-cpp/build/reference/bscmake-options)中的 **\/NOLOGO** 选项。|  
|**TrackerLogDirectory**|可选 **String** 参数。<br /><br /> 指定跟踪器日志目录。|  
  
## 备注  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)