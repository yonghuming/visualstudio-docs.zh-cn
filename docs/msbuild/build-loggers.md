---
title: "生成记录器 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b28a3a7d7412a496802a176f6365e961cd7c2673
ms.lasthandoff: 02/22/2017

---
# <a name="build-loggers"></a>生成记录器
记录器提供一种方法，通过此方法可自定义生成的输出并显示消息、错误或警告以响应特定生成事件。 每个记录器作为 .NET 类实现，该类实现 <xref:Microsoft.Build.Framework.ILogger> 接口，该接口在 Microsoft.Build.Framework.dll 程序集中定义。  
  
 在实现记录器时，有两种方法可供选择：  
  
-   直接实现 <xref:Microsoft.Build.Framework.ILogger> 接口。  
  
-   从帮助程序类 <xref:Microsoft.Build.Utilities.Logger> 中派生类，该帮助程序类定义在 Microsoft.Build.Utilities.dll 程序集中。 <xref:Microsoft.Build.Utilities.Logger> 实现 <xref:Microsoft.Build.Framework.ILogger>，并提供一些 <xref:Microsoft.Build.Framework.ILogger> 成员的默认实现。  
  
 本主题将介绍如何编写派生自 <xref:Microsoft.Build.Utilities.Logger> 的简单记录器，并在控制台上显示信息以响应特定生成事件。  
  
## <a name="registering-for-events"></a>注册事件  
 记录器的目的是收集有关生成进度的信息（正如生成引擎所报告的信息），随后以有用的方式报告该信息。 所有记录器必须替代 <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> 方法，此方法是记录器用于注册事件的方法。 在此示例中，记录器注册 <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>、<xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> 和 <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> 事件。  
  
 [!code-cs[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## <a name="responding-to-events"></a>对事件作出响应  
 记录器注册特定事件后，这些事件出现时，记录器需要处理这些事件。 对于 <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> 和 <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> 事件，记录器仅编写一个短语以及事件涉及的项目文件的名称。 记录器中的所有消息都写入到控制台窗口。  
  
 [!code-cs[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## <a name="responding-to-logger-verbosity-values"></a>响应记录器详细信息值  
 在某些情况下，如果 MSBuild.exe **/verbosity** 开关包含特定值，可能需要仅记录事件中的信息。 在此示例中，如果由 **/verbosity** 开关设置的 <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> 属性等同于 <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`，则 <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> 事件处理程序仅记录一条信息。  
  
 [!code-cs[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## <a name="specifying-a-logger"></a>指定记录器  
 将记录器编译到程序集后，你需要告诉 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 在生成过程中使用该记录器。 可以通过配合使用 **/logger** 开关和 MSBuild.exe 来执行此操作。 有关可用于 MSBuild.exe 的开关的详细信息，请参阅[命令行引用](../msbuild/msbuild-command-line-reference.md)。  
  
 以下命令行生成项目 `MyProject.csproj`，并使用在 `SimpleLogger.dll` 中实现的记录器类。 **/nologo** 开关隐藏版权标志和版权消息，**/noconsolelogger** 开关禁用默认的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 控制台记录器。  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 以下命令行通过相同记录器生成项目，但是 `Verbosity` 级别为 `Detailed`。  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例包含记录器的完整代码。  
  
### <a name="code"></a>代码  
 [!code-cs[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
### <a name="comments"></a>注释  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 以下示例演示如何实现将日志写入到文件的记录器（而非在控制台窗口中显示记录器）。  
  
### <a name="code"></a>代码  
 [!code-cs[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]  
  
### <a name="comments"></a>注释  
  
## <a name="see-also"></a>另请参阅  
 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)
