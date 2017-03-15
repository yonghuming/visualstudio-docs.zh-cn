---
title: "用 MSBuild 获取生成日志 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild，日志记录"
  - "日志记录 [MSBuild]"
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 用 MSBuild 获取生成日志
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用具有 MSBuild 开关，您可以指定要生成数据要查看，并且您是否希望保存数据编译到一个或多个文件。  还可以指定自定义记录器集合生成数据。  有关 MSBuild 本主题并未的命令行开关的信息，请参见 [命令行参考](../msbuild/msbuild-command-line-reference.md)。  
  
> [!NOTE]
>  使用 Visual Studio IDE，如果您生成项目，可以通过查看生成日志中排除某些生成。  有关更多信息，请参见[如何：查看、保存和配置生成日志文件](../ide/how-to-view-save-and-configure-build-log-files.md)。  
  
## 设置详细级别  
 当生成项目使用 MSBuild 时，如果不指定详细级别，下面的消息显示在输出日志：  
  
-   错误、类别如重要的警告和消息。  
  
-   某些状态事件。  
  
-   生成摘要。  
  
 使用 **\/verbosity** \(**\/v**\) 开关，可以控制多少数据显示在输出记录。  对于解决问题，请使用 `detailed` \(`d`\) 或 `diagnostic` \(`diag`\) 的详细级别，提供多数信息。  
  
 生成过程可以较慢的，在设置 **\/verbosity** 到 `detailed` 和较慢时，在设置 **\/verbosity** 到 `diagnostic`时。  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## 保存到文件中生成日志  
 可以使用 **\/fileLogger** \(**fl**\) 开关生成数据保存到文件中。  下面的示例生成数据保存到名为 `msbuild.log`的文件。  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 在下面的示例中，日志文件名为 `MyProjectOutput.log`，并且，日志输出的详细级别设置为 `diagnostic`。  使用 **\/filelogparameters** \(`flp`\) 开关，您指定了两组。  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 有关更多信息，请参见[命令行参考](../msbuild/msbuild-command-line-reference.md)。  
  
## 保存到多个文件的日志输出  
 下面的示例保存整个记录到 `msbuild1.log`，错误。`JustErrors.log`和提醒 `JustWarnings.log`。  该示例对三个文件都使用文件号。  文件号。**\/fl** 和 **\/flp** 开关后指定 \(例如，`/fl1` 和 `/flp1`\)。  
  
 文件、2 和 3 **\/filelogparameters** \(`flp`\) 开关在每个文件中指定要为每个文件以及如何包含。  名称不为文件指定 1，因此，使用 `msbuild1.log` 的默认名称。  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 有关更多信息，请参见[命令行参考](../msbuild/msbuild-command-line-reference.md)。  
  
## 使用自定义记录器  
 您可以通过编写实现 <xref:Microsoft.Build.Framework.ILogger> 接口的托管类型来编写自己的记录器。  可以使用自定义记录器，例如，将发送电子邮件、记录到数据库或记录的生成错误到 XML 文件。  有关更多信息，请参见[生成记录器](../msbuild/build-loggers.md)。  
  
 使用 **\/logger** 开关，在 MSBuild 命令行，您可以指定自定义记录器。  还可以使用 **\/noconsolelogger** 开关禁用默认值控制个记录器。  
  
## 请参阅  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [生成记录器](../msbuild/build-loggers.md)   
 [多处理器环境下的日志记录](../msbuild/logging-in-a-multi-processor-environment.md)   
 [创建转发记录器](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)