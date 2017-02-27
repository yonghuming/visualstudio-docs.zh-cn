---
title: "如何：查看、保存和配置生成日志文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# 如何：查看、保存和配置生成日志文件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当您在 Visual Studio IDE 后生成项目，可以查看有关该生成的信息。**输出** 窗口。  使用此信息，可以，例如，解决生成失败。  对于 C\+\+ 项目，也可以查看在自动创建并保存的 .txt 文件的信息。  对于托管代码项目，可以复制并粘贴从 **输出** 窗口的信息到 .txt 文件并将其保存您。  也可以使用 IDE 指定哪种信息要查看有关每个生成。  
  
 使用 MSBuild，如果正在生成任何项目，可以创建 .txt 文件保存有关生成的信息。  有关更多信息，请参见[获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)。  
  
### 若要查看 c. 的 c\+\+ 生成日志文件项目  
  
1.  在 **Windows 资源管理器** 或 **文件资源管理器**，请打开以下文件：\\..。  \\Visual Studio *版本*\\projects\\*ProjectName*\\*ProjectName*\\debug\\*ProjectName*.txt  
  
### 若要创建托管代码的生成日志文件项目  
  
1.  在菜单栏上，依次选择 **生成**，**生成解决方案**。  
  
2.  在 **输出** 窗口中，将显示生成的信息，然后将其复制到剪贴板。  
  
3.  打开文本编辑器，如"记事本"，信息粘贴到文件中，然后保存该文件。  
  
### 更改在生成日志中包含的信息大小  
  
1.  在菜单栏上，依次选择 **工具**，**选项**。  
  
2.  在 **项目和解决方案** 页上，选择 **生成并运行** 页。  
  
3.  在 **MSBuild 项目生成输出详细信息** 列表中，选择下列值之一，然后选择 **确定** 按钮。  
  
    |详细级别|描述|  
    |----------|--------|  
    |安静|仅显示生成摘要。|  
    |最低|显示生成摘要和错误、类别如重要的警告和消息。|  
    |Normal|显示生成摘要；错误、类别如重要的警告和消息；和生成的主要步骤。  您经常使用此详细程度。|  
    |详细|显示生成摘要；错误、类别如重要的警告和消息；所有生成的步骤；和自一般重要性类别的消息。|  
    |诊断|显示用于生成可用的所有数据。  可以使用此详细级别帮助调试问题与自定义生成脚本，以及其他编译问题。|  
  
     有关更多信息，请参见[选项对话框，项目和解决方案，生成和运行](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)和<xref:Microsoft.Build.Framework.LoggerVerbosity>。  
  
    > [!IMPORTANT]
    >  您必须重新生成您的项目中反映在 **输出** 窗口 \(所有项目\) 和 *ProjectName*.txt 文件 \(仅针对 C\+\+ 项目\)。  
  
## 请参阅  
 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [在 Visual Studio 中生成和清理项目和解决方案](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [在 Visual Studio 中构建应用程序](../ide/compiling-and-building-in-visual-studio.md)