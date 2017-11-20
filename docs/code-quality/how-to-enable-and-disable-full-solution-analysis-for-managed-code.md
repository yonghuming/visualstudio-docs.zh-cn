---
title: "如何： 启用和禁用托管代码的完整解决方案分析 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 94cda949a713a773e5586e5b1ef284c6ba54839c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>如何： 启用和禁用托管代码的完整解决方案分析
> [!NOTE]
>  本主题仅适用于 Visual Studio 2015 Update 3 RC 及更高版本。  
  
 *完整解决方案分析*是 Visual Studio 功能，使你可以选择是否查看仅在打开 Visual C# 或 Visual Basic 文件在你的解决方案，或在你的解决方案中的打开和关闭 Visual C# 或 Visual Basic 文件中的代码分析问题。  
  
 尽管能够看到所有文件中的所有问题很有用，它可以是让人分散注意力并甚至减慢 Visual Studio，如果你的解决方案是非常大，或具有大量的文件。  若要限制显示的问题数和改进 Visual Studio 性能，你可以禁用完整解决方案分析。 如果你想，您便可以轻松地重新启用此功能。  
  
#### <a name="to-toggle-full-solution-analysis"></a>若要切换完整解决方案分析  
  
1.  在 Visual Studio 中的主菜单上，选择**工具**&#124;**选项**查看**选项**对话框。  
  
2.  在**选项**对话框框中，选择**文本编辑器**&#124;**C#**或**基本**&#124;**高级**。  
  
3.  选择**启用完整解决方案分析**复选框以启用完整解决方案分析，或清除相应的框以禁用它。 选择**确定**按钮完成后。  
  
     ![启用完整解决方案分析复选框。] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>启用和禁用完整解决方案分析结果  
 在以下屏幕截图中，你可以启用完整解决方案分析后看到结果。 所有错误和中的代码分析问题*所有*的解决方案中的文件出现，无论这些文件是否是打开。  
  
 ![启用完整解决方案分析。] (../code-quality/media/fsa_enabled.png "FSA_Enabled")  
  
 下面的屏幕截图显示禁用完整解决方案分析后的同一解决方案中的结果。 仅错误和代码分析问题，在错误列表中打开的解决方案文件会出现。  
  
 ![禁用的完整解决方案分析。] (../code-quality/media/fsa_disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>自动禁用完整解决方案分析  
 如果 Visual Studio 检测到 200 MB 或更少的系统内存可供它，它会自动禁用完整解决方案分析 （以及某些其他功能） 如果启用它。 如果发生这种情况，则会出现警报，通知你这些。 按钮可以重新启用完整解决方案分析，如果你想要这样做。  
  
 ![警报文本中挂起完整解决方案分析](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>更多详细信息  
 默认情况下，完整解决方案分析适用于 Visual Basic 启用和禁用对于 Visual C#。  
  
 Visual Studio Update 3 RC 包括增强的代码分析工具诊断 v2 引擎，大大减少内存使用情况和减少了 CPU 时间空闲，即使启用完整解决方案分析。