---
title: "XDCMake 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.xdcmake"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), XDCMake 任务"
  - "XDCMake 任务 (MSBuild (Visual C++))"
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XDCMake 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包装 XML 文档工具 \(xdcmake.exe\)，其将 XML 文档注释 \(.xdc\) 文件合并到 .xml 文件中。  
  
 当在 Visual C\+\+ 源代码中提供了文档注释并通过使用 [\/doc](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp) 编译器选项进行编译时，就创建了 .xdc 文件。  有关更多信息，请参见 [XDCMake 参考](/visual-cpp/ide/xdcmake-reference)、[“XML 文档生成器工具”属性页](/visual-cpp/ide/xml-document-generator-tool-property-pages)和 xdcmake.exe 的命令行帮助选项 \(**\/?**\)。  
  
## 备注  
 默认情况下，xdcmake.exe 工具支持几个命令行选项。  指定 **\/old** 命令行选项则会支持附加选项。  
  
## 参数  
 下表描述了 **XDCMake** 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|**AdditionalDocumentFile**|可选 **String\[\]** 参数。<br /><br /> 指定要合并的一个或多个附加的 .xdc 文件。<br /><br /> 有关更多信息，请参见 [“XML 文档生成器工具”属性页](/visual-cpp/ide/xml-document-generator-tool-property-pages) 中的**“附加文档文件”**说明。  另请参见 **\/old** 和 **\/Fs** 命令行选项获取 xdcmake.exe。|  
|**AdditionalOptions**|可选 **String** 参数。<br /><br /> 命令行中指定的选项的列表。  例如，"*\/option1 \/option2 \/option\#*"。  将此参数用于指定不用任何其他 **XDCMake** 任务参数表示的选项。<br /><br /> 有关更多信息，请参见 [XDCMake 参考](/visual-cpp/ide/xdcmake-reference)、[“XML 文档生成器工具”属性页](/visual-cpp/ide/xml-document-generator-tool-property-pages)和 xdcmake.exe 的命令行帮助 \(**\/?**\)。|  
|**DocumentLibraryDependencies**|可选 **Boolean** 参数。<br /><br /> 如果 `true` 和当前项目在解决方案中静态库 \(.lib\) 项目上有依赖项，则该库项目的 .xdc 文件会包含在当前项目的 .xml 文件输出中。<br /><br /> 有关更多信息，请参见 [“XML 文档生成器工具”属性页](/visual-cpp/ide/xml-document-generator-tool-property-pages)中的**“文档库依赖项”**说明。|  
|**OutputFile**|可选 **String** 参数。<br /><br /> 重写默认输出文件的名称。  默认名称衍生自处理的第一个 .xdc 文件。<br /><br /> 有关更多信息，请参见 [XDCMake 参考](/visual-cpp/ide/xdcmake-reference) 中的 **\/out:**`filename` 选项。  另请参见 **\/old** 和 **\/Fo**  命令行选项获取 xdcmake.exe。|  
|**ProjectName**|可选 **String** 参数。<br /><br /> 当前项目的名称。|  
|**SlashOld**|可选 **Boolean** 参数。<br /><br /> 如果为 `true`，则启用附加 xdcmake.exe 选项。<br /><br /> 有关更多信息，请参见 xdcmake.exe 的 **\/old** 命令行选项。|  
|**Sources**|必选 `ITaskItem[]` 参数。<br /><br /> 定义可以由任务使用和发出的 MSBuild 源文件项数组。|  
|**SuppressStartupBanner**|可选 **Boolean** 参数。<br /><br /> 如果为 `true`，将在任务开始时防止显示版权和版本编号消息。<br /><br /> 有关更多信息，请参见 [XDCMake 参考](/visual-cpp/ide/xdcmake-reference) 中的 **\/nologo** 选项。|  
|**TrackerLogDirectory**|可选 **String** 参数。<br /><br /> 指定跟踪日志的目录。|  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)